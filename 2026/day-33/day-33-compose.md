# Day 33 – Docker Compose: Multi-Container Basics

## Objective
Learn how to deploy and manage single-container and multi-container applications using Docker Compose.

## Tasks Completed

### 1. Install & Verify
- Checked Docker Compose availability.
- Verified the installed Docker Compose version.

### 2. First Compose Application – Nginx
- Created a `compose-basics` directory.
- Created a `docker-compose.yml` file.
- Configured an Nginx service with port mapping.
- Started the container using Docker Compose.
- Accessed the Nginx welcome page through a browser.
- Stopped and removed the services.

### 3. Multi-Container Application – WordPress + MySQL
- Configured WordPress and MySQL services.
- Connected both services using Docker Compose networking.
- Used the MySQL service name for database connectivity.
- Configured a named volume for MySQL data persistence.
- Accessed WordPress through a browser.
- Tested data persistence after restarting the application.

### 4. Docker Compose Commands

| Command | Purpose |
|---|---|
| `docker compose up -d` | Start services in detached mode |
| `docker compose ps` | List running services |
| `docker compose logs -f` | View all service logs |
| `docker compose logs wordpress` | View specific service logs |
| `docker compose stop` | Stop services |
| `docker compose down` | Remove containers and networks |
| `docker compose up -d --build` | Rebuild and start services |

### 5. Environment Variables
- Configured environment variables directly in the Compose YAML file.
- Created a `.env` file.
- Referenced environment variables inside `docker-compose.yml`.
- Verified environment variable configuration.

## Key Learnings

- Docker Compose simplifies multi-container application management.
- Services can communicate using their service names.
- Compose automatically creates a default network.
- Named volumes help preserve database data.
- Environment variables make configuration easier and more flexible.

## Files Created

- `compose-basics/docker-compose.yml`
- `wordpress-mysql/docker-compose.yml`
- `.env`
- `day-33-compose.md`

## Conclusion

Successfully practiced Docker Compose fundamentals and learned how to configure, deploy, monitor, and manage multi-container applications using a single YAML file.

**#90DaysOfDevOps | #Docker | #DockerCompose | #DevOps**
