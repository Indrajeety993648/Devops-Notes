# Docker Volumes

**Date:** 30 November 2024
**Lecture Topic:** Data Persistence

## 1. The Problem
Containers are **ephemeral**. When a container is removed, its writable layer is deleted. Data is lost.

## 2. Solutions: Volumes & Bind Mounts

### Docker Volumes
Managed by Docker. Stored in `/var/lib/docker/volumes/`.
- **Create:** `docker volume create my-vol`
- **Use:** `docker run -v my-vol:/data nginx`
- **Pros:** Best for persistence, easy to backup, independent of host OS.

### Bind Mounts
Maps a host file/directory to the container.
- **Use:** `docker run -v /home/user/code:/app nginx`
- **Pros:** Great for development (edit code on host, see changes in container).

**Visual Representation:**
```mermaid
graph TD
    HostOS[Host Filesystem]
    subgraph Docker Area
    Vol[Volume]
    end
    Container[Container]
    HostPath[/home/user/data]

    Vol -->|Mounts to| Container
    HostPath -->|Bind Mounts to| Container
```

## 3. Tmpfs Mounts
Stored in host memory only. Never written to disk. Good for secrets.
