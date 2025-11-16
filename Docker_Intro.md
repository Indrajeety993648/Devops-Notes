# Introduction to Docker

**Date:** 16 November 2024
**Lecture Topic:** Docker Basics

## 1. What is Docker?
Docker is an open platform for developing, shipping, and running applications. It enables you to separate your applications from your infrastructure so you can deliver software quickly.

## 2. Containers vs. Virtual Machines

| Feature | Virtual Machines | Containers |
| :--- | :--- | :--- |
| **Guest OS** | Complete OS per VM | Shared Host OS Kernel |
| **Isolation** | Hardware-level | Operating System-level |
| **Size** | Gigabytes | Megabytes |
| **Boot up** | Minutes | Seconds |

**Visual Representation:**
```mermaid
graph TD
    subgraph VM_Architecture
    HW1[Hardware] --> HO1[Host OS]
    HO1 --> HV[Hypervisor]
    HV --> GA[Guest OS A]
    HV --> GB[Guest OS B]
    GA --> AppA[App A]
    GB --> AppB[App B]
    end

    subgraph Docker_Architecture
    HW2[Hardware] --> HO2[Host OS]
    HO2 --> DE[Docker Engine]
    DE --> C1[Container A]
    DE --> C2[Container B]
    end
```

## 3. Docker Architecture
- **Client:** The `docker` CLI.
- **Daemon:** The background process (`dockerd`) that manages containers.
- **Registry:** Stores Docker images (e.g., Docker Hub).
