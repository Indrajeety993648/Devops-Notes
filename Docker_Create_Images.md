# Creating Docker Images

**Date:** 23 November 2024
**Lecture Topic:** Building Custom Docker Images

## 1. The Dockerfile
A `Dockerfile` is a text document with instructions to build an image.

### Key Instructions
| Instruction | Purpose |
| :--- | :--- |
| `FROM` | Base image (Start here!) |
| `RUN` | Execute command in layer |
| `COPY` | Copy files from host to image |
| `WORKDIR` | Set working directory |
| `CMD` | Command to run when container starts |
| `EXPOSE` | Document port usage |

### Example Dockerfile
```dockerfile
# Stage 1: Build
FROM node:14 as builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Run
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
```

## 2. Multi-Stage Builds
As seen above, multi-stage builds help reduce image size by excluding build dependencies from the final runtime image.

## 3. Building Context
`docker build -t my-app:v1 .`
- The `.` specifies the **build context** (current directory).
