kind create cluster

kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.19.1/cert-manager.yaml

helm install kserve-crd oci://ghcr.io/kserve/charts/kserve-crd --version v0.15.0

helm install kserve oci://ghcr.io/kserve/charts/kserve --version v0.15.0 \
  --set kserve.controller.deploymentMode=RawDeployment \
  --set kserve.controller.gateway.ingressGateway.enableGatewayApi=true \
  --set kserve.controller.gateway.ingressGateway.createGateway=true \
  --set kserve.controller.gateway.ingressGateway.kserveGateway=kserve/kserve-ingress-gateway


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


# Model Validation Operator

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
```