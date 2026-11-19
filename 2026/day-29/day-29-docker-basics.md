# Day 29 – Introduction to Docker

## 90 Days of DevOps Challenge

### 1. What is Docker?

Docker is an open-source platform that allows developers to build, package, and run applications inside containers.

Containers provide a lightweight and isolated environment with all the dependencies required to run an application.

**Why do we need Docker?**
- Ensures application consistency across different environments.
- Simplifies application deployment.
- Reduces environment-related issues.
- Uses fewer resources compared to Virtual Machines.
- Supports scalability and portability.

### 2. Containers vs Virtual Machines

| Containers | Virtual Machines |
|---|---|
| Lightweight | Heavyweight |
| Share the host OS kernel | Have their own guest OS |
| Start quickly | Take more time to start |
| Require fewer resources | Require more resources |
| Application-level isolation | Hardware-level virtualization |

### 3. Docker Architecture

Docker follows a client-server architecture.

**Main Components:**

- **Docker Client:** Allows users to interact with Docker using commands.
- **Docker Daemon:** Manages images, containers, networks, and volumes.
- **Docker Images:** Read-only templates used to create containers.
- **Docker Containers:** Running instances of Docker images.
- **Docker Registry:** Stores and distributes Docker images, such as Docker Hub.

**Architecture Flow:**

Docker Client → Docker Daemon → Docker Images → Docker Containers

Docker Registry provides images that can be downloaded and used to create containers.

### 4. Docker Installation and Verification

Verified Docker installation using:

```bash
docker --version
docker info
```

Ran the first Docker container:

```bash
docker run hello-world
```

**Result:** Successfully executed the Hello World container.

### 5. Running Nginx Container

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Accessed the Nginx web server through:

```text
http://localhost:8080
```

**Result:** Successfully accessed the Nginx welcome page in the browser.

### 6. Running Ubuntu Container

```bash
docker run -it --name my-ubuntu ubuntu bash
```

Explored the Ubuntu environment using:

```bash
whoami
pwd
ls
cat /etc/os-release
```

Exited the container using:

```bash
exit
```

### 7. Container Management

**List running containers:**

```bash
docker ps
```

**List all containers:**

```bash
docker ps -a
```

**Stop a container:**

```bash
docker stop my-nginx
```

**Remove a container:**

```bash
docker rm my-nginx
```

### 8. Exploring Docker Features

**Detached Mode:**

```bash
docker run -d nginx
```

Runs the container in the background.

**Custom Container Name:**

```bash
docker run -d --name web-server nginx
```

**Port Mapping:**

```bash
docker run -d --name nginx-server -p 8080:80 nginx
```

**Check Container Logs:**

```bash
docker logs nginx-server
```

**Execute Commands Inside a Running Container:**

```bash
docker exec -it nginx-server bash
```

### 9. Important Docker Commands

| Command | Purpose |
|---|---|
| docker images | List images |
| docker pull | Download an image |
| docker run | Create and start a container |
| docker ps | List running containers |
| docker ps -a | List all containers |
| docker stop | Stop a container |
| docker start | Start a container |
| docker rm | Remove a container |
| docker logs | View container logs |
| docker exec | Execute commands inside a container |

### 10. Key Learnings

- Understood Docker and containerization.
- Learned the difference between containers and virtual machines.
- Explored Docker architecture and its components.
- Installed and verified Docker.
- Successfully ran Hello World, Nginx, and Ubuntu containers.
- Practiced container management and essential Docker commands.
- Explored port mapping, detached mode, logs, and Docker Exec.

### Conclusion

Day 29 helped me understand the fundamentals of Docker and containerization through hands-on practice.

Docker is an essential technology in modern DevOps workflows, application deployment, CI/CD pipelines, and Kubernetes.

**Next Step:** Continue learning Docker images, volumes, networking, and Docker Compose.

#90DaysOfDevOps #Docker #DevOps #TrainWithShubham
