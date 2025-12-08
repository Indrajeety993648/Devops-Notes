# Deep Dive into Kubernetes Replicasets

**Date:** 08 December 2024
**Lecture Topic:** Scaling with Replicasets

## 1. Purpose
A ReplicaSet ensures that a specified number of pod replicas are running at any given time. It is used for:
- Redundancy (High Availability).
- Scaling (Load distribution).

## 2. Selectors
ReplicaSet uses **Labels** and **Selectors** to track pods.
- `matchLabels`: Identify which pods belong to this RS.

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: frontend-rs
spec:
  replicas: 3
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: php-redis
        image: gcr.io/google_samples/gb-frontend:v3
```

## 3. Scaling
- Imperative: `kubectl scale rs frontend-rs --replicas=5`
- Declarative: Edit YAML and `kubectl apply -f rs.yaml`.
