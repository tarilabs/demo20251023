
```sh
kind create cluster

kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.19.1/cert-manager.yaml

helm install kserve-crd oci://ghcr.io/kserve/charts/kserve-crd --version v0.15.0

helm install kserve oci://ghcr.io/kserve/charts/kserve --version v0.15.0 \
  --set kserve.controller.deploymentMode=RawDeployment \
  --set kserve.controller.gateway.ingressGateway.createGateway=true 
```

not used:
  --set kserve.controller.gateway.ingressGateway.enableGatewayApi=true \
  --set kserve.controller.gateway.ingressGateway.kserveGateway=kserve/kserve-ingress-gateway

```sh
# Script to enable Modelcars
# Fetch the current storageInitializer configuration
config=$(kubectl get configmap inferenceservice-config -n default -o jsonpath='{.data.storageInitializer}')
# Enable modelcars and set the UID for the containers to run (required for minikube)
newValue=$(echo $config | jq -c '. + {"enableModelcar": true, "uidModelcar": 1010}')

# Create a temporary directory for the patch file
tmpdir=$(mktemp -d)
cat <<EOT > $tmpdir/patch.txt
[{
  "op": "replace",
  "path": "/data/storageInitializer",
  "value": '$newValue'
}]
EOT

# Apply the patch to the ConfigMap
kubectl patch configmap -n default inferenceservice-config --type=json --patch-file=$tmpdir/patch.txt

# Restart the KServe controller to apply changes
kubectl delete pod -n default -l control-plane=kserve-controller-manager
```

OK the above ^

### Validaton policy

```sh
kubectl apply -f validatingpolicy.yaml 
```

```sh
kubectl apply -f - <<EOF
apiVersion: serving.kserve.io/v1beta1
kind: InferenceService
metadata:
  name: my-inference-service
spec:
  predictor:
    model:
      modelFormat:
        name: sklearn
      storageUri: hf://untrusted/model
EOF
```

Results in:

```
The inferenceservices "my-inference-service" is invalid: : ValidatingAdmissionPolicy 'restrict-kserve-model-uri' with binding 'restrict-kserve-model-uri-binding' denied request: storageUri must start with 'oci://quay.io/mmortari' or 'hf://mmortari'
```

as expected.

<!-- # Model Validation Operator ATTEMPT 1

```diff
diff --git a/Makefile b/Makefile
index 46f203d..2fd8437 100644
--- a/Makefile
+++ b/Makefile
@@ -53,7 +53,7 @@ endif
 # This is useful for CI or a project to utilize a specific version of the operator-sdk toolkit.
 OPERATOR_SDK_VERSION ?= v1.41.1
 # Image URL to use all building/pushing image targets
-IMG ?= controller:latest
+IMG ?= ghcr.io/sigstore/model-validation-operator:v0.0.1
 
 # Get the currently used golang install path (in GOPATH/bin, unless GOBIN is set)
 ifeq (,$(shell go env GOBIN))
@@ -182,7 +182,7 @@ generate-local-certs: ## Generate TLS certificates for local development
 # More info: https://docs.docker.com/develop/develop-images/build_enhancements/
 .PHONY: docker-build
 docker-build: test ## Build docker image with the manager.
-       $(CONTAINER_TOOL) build -t ${IMG} -f ${CONTAINER_FILE} .
+       $(CONTAINER_TOOL) build --load -t ${IMG} -f ${CONTAINER_FILE} .
 
 .PHONY: docker-push
 docker-push: ## Push docker image with the manager.
```

```sh
make docker-build
kind load docker-image ghcr.io/sigstore/model-validation-operator:v0.0.1
```

```sh
source venv/bin/activate
pip install model-signing
``` -->

# Model Validation Operator ATTEMPT 2

Model on HF with:

```sh
mkdir model-joblib/.cache # hack/workaround
model_signing sign sigstore --ignore-paths model-joblib/.cache model-joblib
cat model-joblib/model.sig | jq -r '.dsseEnvelope.payload' | base64 -d | jq '.predicate.serialization.ignore_paths'
cd model-joblib
hf upload tarilabs/model-joblib .
```

```sh
git checkout securesign/main
./install-kind.sh
```

poi

```sh
kubectl apply -f modelvalidation.yaml
kubectl apply -f isvc.yaml
```

### Sigstory Policy Controller check the ModelCar image has MY signature

```sh
helm repo add sigstore https://sigstore.github.io/helm-charts
helm install policy-controller sigstore/policy-controller -n cosign-system --create-namespace
kubectl label namespace default policy.sigstore.dev/include=true
```

LAST ONE super important to make sure the NS is actually checked by the controller

Keyless sign:
```sh
cosign sign quay.io/mmortari/demo20241108-base:modelcar-busybox
```

NOTE: best use SHA not the tag, but okay for the purpose of this demo

Using "borked" clusterimagepolicy:

```sh
kubectl describe rs/my-inference-service-predictor-6b88b9bb64 # <-- might change
kubectl describe deployment/my-inference-service-predictor
kubectl get deployment my-inference-service-predictor -o yaml | yq .status.conditions
```

receiving

```yaml
- lastTransitionTime: "2025-11-05T18:15:47Z"
  lastUpdateTime: "2025-11-05T18:15:47Z"
  message: |-
    admission webhook "policy.sigstore.dev" denied the request: validation failed: failed policy: require-mmortari-keyless: spec.containers[1].image, spec.initContainers[0].image
    quay.io/mmortari/demo20241108-base:modelcar-busybox@sha256:4bf421130853c663edf969b4e7577bfc7165b4b9d2eb3f3c0b54bdf3466a7968 signature keyless validation failed for authority authority-0 for quay.io/mmortari/demo20241108-base@sha256:4bf421130853c663edf969b4e7577bfc7165b4b9d2eb3f3c0b54bdf3466a7968: no matching signatures: none of the expected identities matched what was in the certificate, got subjects [matteo.mortari@gmail.com] with issuer https://accounts.google.com
  reason: FailedCreate
  status: "True"
  type: ReplicaFailure
```

Because while the Signature is there:

```
cosign tree quay.io/mmortari/demo20241108-base:modelcar-busybox
📦 Supply Chain Security Related artifacts for an image: quay.io/mmortari/demo20241108-base:modelcar-busybox
└── 🔐 Signatures for an image tag: quay.io/mmortari/demo20241108-base:sha256-4bf421130853c663edf969b4e7577bfc7165b4b9d2eb3f3c0b54bdf3466a7968.sig
   └── 🍒 sha256:79be6a6aea25703dc9825b10ed8e92b250bf76e772da19fd817d3ac144ff1c4e
```

I did asked for:

```yaml
  images:
    - glob: "quay.io/mmortari/*"
  authorities:
    - keyless:
        identities:
          - issuer: "https://accounts.google.com"
            subject: "uknown@gmail.com"
```

But when the clusterimagepolicy is correct:

```yaml
apiVersion: policy.sigstore.dev/v1beta1
kind: ClusterImagePolicy
metadata:
  name: require-mmortari-keyless
spec:
  images:
    - glob: "quay.io/mmortari/*"
  authorities:
    - keyless:
        identities:
          - issuer: "https://accounts.google.com"
            subject: "matteo.mortari@gmail.com"
```

Then all works as expected:

```
kubectl describe isvc
Name:         my-inference-service
Namespace:    default
Labels:       <none>
Annotations:  serving.kserve.io/deploymentMode: RawDeployment
API Version:  serving.kserve.io/v1beta1
Kind:         InferenceService
Metadata:
  Creation Timestamp:  2025-11-05T18:30:07Z
  Finalizers:
    inferenceservice.finalizers
  Generation:        1
  Resource Version:  63570
  UID:               3dd50148-f9fb-4d1b-9805-17722f70b4f8
Spec:
  Predictor:
    Model:
      Model Format:
        Name:  sklearn
      Name:    
      Resources:
      Storage Uri:  oci://quay.io/mmortari/demo20241108-base:modelcar-busybox
Status:
  Address:
    URL:  http://my-inference-service-predictor.default.svc.cluster.local
  Components:
    Predictor:
      URL:  http://my-inference-service-predictor-default.example.com
  Conditions:
    Last Transition Time:  2025-11-05T18:31:38Z
    Status:                True
    Type:                  IngressReady
    Last Transition Time:  2025-11-05T18:31:38Z
    Status:                True
    Type:                  PredictorReady
    Last Transition Time:  2025-11-05T18:31:38Z
    Status:                True
    Type:                  Ready
  Model Status:
    Copies:
      Failed Copies:  0
      Total Copies:   1
    States:
      Active Model State:  Loaded
      Target Model State:  Loaded
    Transition Status:     UpToDate
  Observed Generation:     1
  URL:                     http://my-inference-service-default.example.com
Events:
  Type    Reason                 Age   From                Message
  ----    ------                 ----  ----                -------
  Normal  InferenceServiceReady  22m   v1beta1Controllers  InferenceService [my-inference-service] is Ready
```
