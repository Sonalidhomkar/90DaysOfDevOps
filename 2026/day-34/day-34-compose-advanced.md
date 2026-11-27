# Day 34 – Docker Compose: Advanced Multi-Container Applications

## Overview
Today, I explored advanced Docker Compose concepts by building a real-world multi-container application stack.

The objective was to understand how multiple services communicate, manage dependencies, handle failures, and maintain persistent data using Docker Compose.

## Key Learnings

### 1. Multi-Service Application Stack
- Created a three-service application using Flask, MySQL/PostgreSQL, and Redis.
- Configured services using `docker-compose.yml`.
- Built a custom Docker image using a Dockerfile.

### 2. Dependencies & Healthchecks
- Implemented `depends_on` to manage service startup order.
- Configured database healthchecks.
- Used `condition: service_healthy` to ensure the database was ready before starting the web application.

### 3. Restart Policies
Explored different Docker restart policies:
- `always` – Automatically restarts the container.
- `on-failure` – Restarts the container when it exits with a non-zero status.
- Understood when to use different restart policies.

### 4. Custom Dockerfiles
- Used `build:` in Docker Compose.
- Modified application code.
- Rebuilt and restarted services using:

```bash
docker compose up --build
```

### 5. Networks, Volumes & Labels
- Created custom Docker networks.
- Configured named volumes for database persistence.
- Added labels to organize services.

### 6. Scaling
- Explored scaling web application containers.
- Learned about port mapping limitations when running multiple replicas.

## Important Commands

```bash
docker compose up -d
docker compose ps
docker compose logs
docker compose down
docker compose up --build
docker compose up --scale web=3 -d
docker compose down -v
```

## Key Takeaways

Today's practice helped me understand how Docker Compose manages multi-container applications, service dependencies, healthchecks, restart policies, networking, persistent storage, and scaling.

These concepts are important for building reliable and maintainable containerized applications.

## Day 34 Completed
Continuing my journey towards becoming a DevOps & Cloud Engineer.

#90DaysOfDevOps #Docker #DockerCompose #DevOps #TrainWithShubham #DevOpsKaJosh
