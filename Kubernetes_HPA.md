# Understanding HPA (Horizontal Pod Autoscaler)

**Date:** 22 December 2024
**Lecture Topic:** Autoscaling

## 1. What is HPA?
HPA automatically scales the number of pods in a deployment based on observed CPU utilization (or custom metrics).

## 2. How it works
- **Metrics Server:** Must be installed to provide resource usage stats.
- **HPA Controller:** Checks metrics every 15 seconds.

## 3. Configuration
```yaml
apiVersion: autoscaling/v1
kind: HorizontalPodAutoscaler
metadata:
  name: php-apache
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: php-apache
  minReplicas: 1
  maxReplicas: 10
  targetCPUUtilizationPercentage: 50
```
