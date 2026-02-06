# 🐳 Docker Commands – Complete Cheat Sheet

This repository contains a **complete Docker commands cheat sheet** written in **easy English**.  
It is useful for **revision**, **hands-on practice**, and **interview preparation**.

---

## 🔹 1. Docker Basics

```bash
docker --version
docker version
docker info
```

👉 Used to check Docker version and system information.

---

## 🔹 2. Docker Images Commands

### List Images

```bash
docker images
docker image ls
```

### Pull Image from Docker Hub

```bash
docker pull ubuntu
docker pull nginx:latest
```

### Remove Image

```bash
docker rmi image_id
docker rmi ubuntu
```

### Remove All Images

```bash
docker rmi $(docker images -q)
```

### Build Image from Dockerfile

```bash
docker build -t myimage .
```

---

## 🔹 3. Docker Containers Commands

### List Containers

```bash
docker ps          # running containers
docker ps -a       # all containers
```

### Create & Run Container

```bash
docker run nginx
docker run -it ubuntu
docker run -d nginx
```

### Run with Name

```bash
docker run --name mycontainer nginx
```

### Run with Port Mapping

```bash
docker run -p 8080:80 nginx
```

### Run in Background (Detached Mode)

```bash
docker run -d nginx
```

---

## 🔹 4. Start / Stop / Restart Containers

```bash
docker start container_id
docker stop container_id
docker restart container_id
```

---

## 🔹 5. Remove Containers

```bash
docker rm container_id
docker rm mycontainer
```

### Remove All Stopped Containers

```bash
docker container prune
```

---

## 🔹 6. Container Logs & Inspection

### View Logs

```bash
docker logs container_id
```

### Live Logs

```bash
docker logs -f container_id
```

### Inspect Container Details

```bash
docker inspect container_id
```

---

## 🔹 7. Execute Commands Inside Container

```bash
docker exec -it container_id bash
docker exec -it container_id sh
```

👉 Used to enter a running container.

---

## 🔹 8. Docker Volumes Commands

### List Volumes

```bash
docker volume ls
```

### Create Volume

```bash
docker volume create myvolume
```

### Use Volume with Container

```bash
docker run -v myvolume:/data ubuntu
```

### Remove Volume

```bash
docker volume rm myvolume
```

---

## 🔹 9. Docker Networks Commands

### List Networks

```bash
docker network ls
```

### Create Network

```bash
docker network create mynetwork
```

### Run Container with Network

```bash
docker run --network mynetwork nginx
```

### Remove Network

```bash
docker network rm mynetwork
```

---

## 🔹 10. Docker System Cleanup

### Remove Unused Data

```bash
docker system prune
```

### Remove Everything (Images, Containers, Volumes)

```bash
docker system prune -a
```

---

## 🔹 11. Docker Tag & Push (Docker Registry)

### Tag Image

```bash
docker tag myimage username/myimage
```

### Login to Docker Hub

```bash
docker login
```

### Push Image

```bash
docker push username/myimage
```

---

## 🔹 12. Dockerfile Related Commands

```bash
docker build -t app .
docker run app
```

### Common Dockerfile Instructions

```
FROM
RUN
COPY
ADD
CMD
ENTRYPOINT
EXPOSE
WORKDIR
ENV
```

---

## 🔹 13. Docker Compose Commands

```bash
docker-compose up
docker-compose up -d
docker-compose down
docker-compose ps
docker-compose logs
```

---

## 🔹 14. Important One-Line Interview Commands ⭐

```bash
docker ps
docker images
docker run -it ubuntu
docker exec -it container bash
docker logs container
docker build -t image .
docker system prune
```

---

## 🔹 15. Very Short Summary (For Interviews)

- **Image** → Blueprint
- **Container** → Running instance
- `docker run` → Create + start container
- `docker exec` → Enter running container
- `docker ps` → List containers
- `docker images` → List images

```

```
