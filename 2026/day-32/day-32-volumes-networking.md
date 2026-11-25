# Day 32 – Docker Volumes & Networking

## Objective
Today's challenge focused on understanding Docker data persistence and container-to-container communication using Docker Volumes, Bind Mounts, and Docker Networks.

## 1. Understanding Data Persistence

Containers are ephemeral by nature. When a container is removed, the data stored in its writable container layer is also lost.

**Observation:**
- Created a database container.
- Inserted sample records into the database.
- Removed the container.
- Started a new container without attaching a volume.
- The previously stored data was not available.

**Learning:** Container storage is temporary. Docker volumes help preserve important data even after container removal.

## 2. Docker Named Volumes

Commands used:

```bash
docker volume create my-db-volume
docker volume ls
docker volume inspect my-db-volume
```

Attached the volume to a database container:

```bash
docker run -d \
  --name mysql-db \
  -e MYSQL_ROOT_PASSWORD=Root12345 \
  -e MYSQL_DATABASE=testdb \
  -v my-db-volume:/var/lib/mysql \
  mysql:8.0
```

**Observation:**
- Created a named Docker volume.
- Attached it to the MySQL container.
- Inserted sample database records.
- Removed the container.
- Created another container using the same volume.
- Verified that the previous data was still available.

**Learning:** Named volumes provide persistent storage independent of a container's lifecycle.

## 3. Docker Bind Mounts

Created a host directory and an HTML file.

```bash
mkdir docker-web
cd docker-web
```

Created `index.html` and started an Nginx container:

```bash
docker run -d \
  --name nginx-web \
  -p 8080:80 \
  -v "$(pwd):/usr/share/nginx/html" \
  nginx
```

Opened the application:

```text
http://localhost:8080
```

Updated the HTML file on the host machine and refreshed the browser.

**Observation:** Changes made to the host file were reflected in the browser.

**Named Volume vs Bind Mount:**

| Named Volume | Bind Mount |
|---|---|
| Managed by Docker | Uses a specific host path |
| Docker manages its storage location | User specifies the host directory |
| Useful for persistent application data | Useful for development and file sharing |

## 4. Docker Networking Basics

Commands used:

```bash
docker network ls
docker network inspect bridge
```

**Observation:**
- Inspected Docker's default bridge network.
- Tested communication between containers using IP addresses.
- Tested communication using container names.
- Default bridge networking does not provide automatic container-name resolution.

## 5. Custom Docker Networks

Created a custom bridge network:

```bash
docker network create my-app-net
```

Started two containers:

```bash
docker run -dit --name container1 --network my-app-net alpine sh

docker run -dit --name container2 --network my-app-net alpine sh
```

Tested name-based communication:

```bash
docker exec container1 ping -c 4 container2
```

**Observation:** Containers connected to the same custom bridge network can communicate with each other using container names through Docker's embedded DNS.

## 6. Database and Application Communication

Created a custom network and attached a database container with persistent storage.

```bash
docker network create app-network

docker volume create mysql-data

docker run -d \
  --name mysql-db \
  --network app-network \
  -e MYSQL_ROOT_PASSWORD=Root12345 \
  -e MYSQL_DATABASE=appdb \
  -v mysql-data:/var/lib/mysql \
  mysql:8.0
```

Started an application-side test container:

```bash
docker run -dit \
  --name app-container \
  --network app-network \
  alpine sh
```

Installed a network testing utility and tested connectivity:

```bash
docker exec app-container sh -c "apk add --no-cache busybox-extras"
docker exec app-container ping -c 4 mysql-db
```

**Expected Result:** Successful communication with the database container using its container name.

Note: This verifies network connectivity, not a complete MySQL application connection.

## Key Learnings

1. Containers are temporary, but volumes provide persistent data storage.
2. Named volumes are managed by Docker.
3. Bind mounts connect host directories with container directories.
4. Docker networks enable communication between containers.
5. Custom bridge networks support container-name resolution.
6. Database containers can use persistent volumes for data protection.
7. Docker networking is essential for multi-container applications.

## Conclusion

Day 32 helped me understand two important Docker concepts: data persistence and container networking.

I learned how to preserve database data using named volumes, share files using bind mounts, and establish communication between containers using custom bridge networks.

**Hands-on practice is helping me build a stronger foundation in Docker and DevOps!**

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham #Docker #DockerVolumes #DockerNetworking #DevOpsLearning
