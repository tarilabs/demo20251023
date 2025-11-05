con

```
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
            subject: "unknown@gmail.com"
---
apiVersion: policy.sigstore.dev/v1beta1
kind: ClusterImagePolicy
metadata:
  name: allow-everything
spec:
  images:
    - glob: "**"
  authorities:
    - static:
        action: pass

```


```
demo20251023 % kubectl describe rs/my-inference-service-predictor-6b88b9bb64
Name:           my-inference-service-predictor-6b88b9bb64
Namespace:      default
Selector:       app=isvc.my-inference-service-predictor,pod-template-hash=6b88b9bb64
Labels:         app=isvc.my-inference-service-predictor
                component=predictor
                pod-template-hash=6b88b9bb64
                serving.kserve.io/inferenceservice=my-inference-service
Annotations:    deployment.kubernetes.io/desired-replicas: 1
                deployment.kubernetes.io/max-replicas: 2
                deployment.kubernetes.io/revision: 1
                internal.serving.kserve.io/storage-initializer-sourceuri: oci://quay.io/mmortari/demo20241108-base:modelcar-busybox
                prometheus.kserve.io/path: /metrics
                prometheus.kserve.io/port: 8080
                serving.kserve.io/deploymentMode: RawDeployment
Controlled By:  Deployment/my-inference-service-predictor
Replicas:       0 current / 1 desired
Pods Status:    0 Running / 0 Waiting / 0 Succeeded / 0 Failed
Pod Template:
  Labels:       app=isvc.my-inference-service-predictor
                component=predictor
                pod-template-hash=6b88b9bb64
                serving.kserve.io/inferenceservice=my-inference-service
  Annotations:  internal.serving.kserve.io/storage-initializer-sourceuri: oci://quay.io/mmortari/demo20241108-base:modelcar-busybox
                prometheus.kserve.io/path: /metrics
                prometheus.kserve.io/port: 8080
                serving.kserve.io/deploymentMode: RawDeployment
  Containers:
   kserve-container:
    Image:      index.docker.io/kserve/sklearnserver:v0.15.0@sha256:d19adc0a6223d72e371a9cf852c56c910789ef0eac6a8baf96db35d0cc1d8304
    Port:       <none>
    Host Port:  <none>
    Args:
      --model_name=my-inference-service
      --model_dir=/mnt/models
      --http_port=8080
    Limits:
      cpu:     1
      memory:  2Gi
    Requests:
      cpu:         1
      memory:      2Gi
    Readiness:     tcp-socket :8080 delay=0s timeout=1s period=10s #success=1 #failure=3
    Environment:   <none>
    Mounts:        <none>
  Volumes:         <none>
  Node-Selectors:  <none>
  Tolerations:     <none>
Conditions:
  Type             Status  Reason
  ----             ------  ------
  ReplicaFailure   True    FailedCreate
Events:
  Type     Reason        Age                 From                   Message
  ----     ------        ----                ----                   -------
  Warning  FailedCreate  29s (x14 over 91s)  replicaset-controller  Error creating: admission webhook "policy.sigstore.dev" denied the request: validation failed: failed policy: require-mmortari-keyless: spec.containers[1].image, spec.initContainers[0].image
quay.io/mmortari/demo20241108-base:modelcar-busybox@sha256:4bf421130853c663edf969b4e7577bfc7165b4b9d2eb3f3c0b54bdf3466a7968 signature keyless validation failed for authority authority-0 for quay.io/mmortari/demo20241108-base@sha256:4bf421130853c663edf969b4e7577bfc7165b4b9d2eb3f3c0b54bdf3466a7968: no matching signatures: none of the expected identities matched what was in the certificate, got subjects [matteo.mortari@gmail.com] with issuer https://accounts.google.com
```

```
- lastTransitionTime: "2025-11-05T18:15:44Z"
  lastUpdateTime: "2025-11-05T18:15:44Z"
  message: Created new replica set "my-inference-service-predictor-6b88b9bb64"
  reason: NewReplicaSetCreated
  status: "True"
  type: Progressing
- lastTransitionTime: "2025-11-05T18:15:44Z"
  lastUpdateTime: "2025-11-05T18:15:44Z"
  message: Deployment does not have minimum availability.
  reason: MinimumReplicasUnavailable
  status: "False"
  type: Available
- lastTransitionTime: "2025-11-05T18:15:47Z"
  lastUpdateTime: "2025-11-05T18:15:47Z"
  message: |-
    admission webhook "policy.sigstore.dev" denied the request: validation failed: failed policy: require-mmortari-keyless: spec.containers[1].image, spec.initContainers[0].image
    quay.io/mmortari/demo20241108-base:modelcar-busybox@sha256:4bf421130853c663edf969b4e7577bfc7165b4b9d2eb3f3c0b54bdf3466a7968 signature keyless validation failed for authority authority-0 for quay.io/mmortari/demo20241108-base@sha256:4bf421130853c663edf969b4e7577bfc7165b4b9d2eb3f3c0b54bdf3466a7968: no matching signatures: none of the expected identities matched what was in the certificate, got subjects [matteo.mortari@gmail.com] with issuer https://accounts.google.com
  reason: FailedCreate
  status: "True"
  type: ReplicaFailure
```

con

