# Day 30 – Docker Images & Container Lifecycle

## Overview
Today, I learned about Docker Images, Image Layers, and Container Lifecycle through hands-on practice.

## Topics Covered

### 1. Docker Images
- Pulled Nginx, Ubuntu, and Alpine images.
- Listed available images using `docker images`.
- Compared Ubuntu and Alpine image sizes.
- Inspected images using `docker image inspect`.
- Practiced removing unused images.

### 2. Docker Image Layers
- Explored image history using `docker image history nginx`.
- Understood Docker image layers.
- Learned how layer caching helps optimize image builds and reduce unnecessary work.

### 3. Container Lifecycle
Practiced the following commands:

- `docker create`
- `docker start`
- `docker pause`
- `docker unpause`
- `docker stop`
- `docker restart`
- `docker kill`
- `docker rm`

Verified container states using `docker ps -a`.

### 4. Working with Running Containers
- Ran Nginx in detached mode.
- Viewed container logs using `docker logs`.
- Followed real-time logs using `docker logs -f`.
- Accessed containers using `docker exec`.
- Executed commands inside running containers.
- Inspected IP addresses, port mappings, and mounts using `docker inspect`.

### 5. Docker Cleanup
- Stopped running containers.
- Removed stopped containers.
- Removed unused images.
- Checked Docker disk usage using `docker system df`.

## Key Learnings
- Difference between Docker images and containers.
- Understanding image layers and caching.
- Managing the complete container lifecycle.
- Monitoring and inspecting running containers.
- Cleaning up unused Docker resources.

## Conclusion
Day 30 helped me strengthen my practical understanding of Docker images and container management.

Learning by doing and staying consistent! 🚀

#90DaysOfDevOps #Docker #DevOps #TrainWithShubham
