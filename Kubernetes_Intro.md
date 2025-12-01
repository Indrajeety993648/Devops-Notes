# Introduction to Orchestration using Kubernetes

**Date:** 01 December 2024
**Lecture Topic:** Kubernetes Architecture

## 1. What is Orchestration?
Managing hundreds of containers manually is impossible. Orchestration automates:
- Provisioning and deployment
- Scaling
- Health monitoring
- Load balancing

## 2. Kubernetes Architecture
Kubernetes (K8s) follows a Master-Worker architecture.

### Control Plane (Master Node)
Responsible for maintaining the desired state.
- **API Server:** The entry point (REST).
- **Etcd:** Key-value store for cluster data (Source of Truth).
- **Scheduler:** Decides where to run pods.
- **Controller Manager:** Detects state changes.

### Worker Node
Runs the applications.
- **Kubelet:** Agent that talks to API Server.
- **Kube-proxy:** Handles networking.
- **Container Runtime:** Docker/Containerd.

**Visual Representation:**
```mermaid
graph TD
    subgraph Master Node
    API[API Server]
    Etcd[(Etcd)]
    Sched[Scheduler]
    CM[Controller Mgr]
    end

    subgraph Worker Node 1
    Kubelet1[Kubelet]
    Proxy1[Kube-proxy]
    Pod1[Pod]
    end

    subgraph Worker Node 2
    Kubelet2[Kubelet]
    Proxy2[Kube-proxy]
    Pod2[Pod]
    end

    API --> Etcd
    API --> Sched
    API --> CM
    API --> Kubelet1
    API --> Kubelet2
```
