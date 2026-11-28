# Day 35 – Multi-Stage Builds & Docker Hub

## Objective

The objective of Day 35 was to understand Docker multi-stage builds, optimize Docker image sizes, and learn how to publish and distribute Docker images using Docker Hub.

## 1. Single-Stage Build

A single-stage Docker build uses one base image for both building and running an application.

### Key Points
- Build and runtime dependencies are included in the same image.
- The final image may contain unnecessary tools and files.
- Image size can be larger.

## 2. Multi-Stage Build

Multi-stage builds use multiple `FROM` instructions in a Dockerfile.

### Key Points
- The first stage builds the application.
- The second stage contains only the required runtime files.
- Build tools and unnecessary dependencies are excluded from the final image.
- Helps reduce image size and improve security.

### Example

```dockerfile
# Stage 1: Build
FROM golang:1.25-alpine AS builder

WORKDIR /app

COPY main.go .

RUN go build -o app main.go

# Stage 2: Runtime
FROM alpine:3.22

WORKDIR /app

COPY --from=builder /app/app .

RUN adduser -D appuser

USER appuser

CMD ["./app"]
```

## 3. Docker Hub

Docker Hub is a cloud-based container registry used to store, manage, and share Docker images.

### Commands

Login:

```bash
docker login
```

Build image:

```bash
docker build -t myapp:v1 .
```

Tag image:

```bash
docker tag myapp:v1 YOUR_USERNAME/myapp:v1
```

Push image:

```bash
docker push YOUR_USERNAME/myapp:v1
```

Pull image:

```bash
docker pull YOUR_USERNAME/myapp:v1
```

## 4. Docker Image Best Practices

- Use lightweight base images such as Alpine when appropriate.
- Use multi-stage builds to remove unnecessary build dependencies.
- Avoid running containers as root.
- Combine related RUN commands to reduce unnecessary layers.
- Use specific image versions instead of `latest`.
- Keep the final image simple and secure.

## 5. Image Size Comparison

Record your actual results after building both images.

| Build Type | Image Size |
|---|---|
| Single-Stage | Add actual size |
| Multi-Stage | Add actual size |

**Observation:** Multi-stage builds can significantly reduce image size because the final stage contains only the application and the dependencies required to run it.

## 6. Docker Hub Repository

Docker Hub Repository: ADD YOUR REPOSITORY LINK

## 7. Key Learnings

1. Understood the difference between single-stage and multi-stage builds.
2. Learned how to optimize Docker images.
3. Practiced Docker Hub authentication and image publishing.
4. Understood image tagging and version management.
5. Learned important Docker security and optimization practices.

## Conclusion

Today's hands-on practice helped me understand how multi-stage builds improve Docker image efficiency and how Docker Hub makes container image distribution easier.

**Day 35 Completed – 90 Days of DevOps!**
