# Deep Dive into Kubernetes Pods

**Date:** 07 December 2024
**Lecture Topic:** Understanding Pods

## 1. What is a Pod?
A Pod is the smallest deployable unit in K8s. It represents a single instance of a running process in your cluster.
- Pods can contain one or more containers (e.g., App + Sidecar).
- Containers in a pod share IP address and Volume.

## 2. YAML Manifest
We define pods using YAML.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: backend
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

## 3. Pod Lifecycle
- **Pending:** Accepted but not started.
- **Running:** At least one container is running.
- **Succeeded:** Terminated with exit code 0.
- **Failed:** Terminated with error.
- **CrashLoopBackOff:** Container keeps failing and restarting.

## 4. Commands
- `kubectl apply -f pod.yaml`: Create pod.
- `kubectl get pods`: List pods.
- `kubectl describe pod <name>`: Debugging.
- `kubectl logs <name>`: View logs.
- `kubectl exec -it <name> -- /bin/bash`: Enter pod.
