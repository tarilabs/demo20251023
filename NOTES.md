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


