
# 🐳 Docker Troubleshooting Commands (Most Common Issues)

This document covers **Docker troubleshooting using commands**, written in **easy English**,  
**interview-oriented**, and **hands-on focused**.

Think of this as: **problem → command → fix**

(For containers, images, network, volumes, ports, build issues)

---

## 🔴 1. Container is NOT Running

### Check container status

```bash
docker ps -a
````

👉 Shows **Exited**, **Created**, **Paused**, etc.

### See why it stopped

```bash
docker logs container_id
```

📌 Common reasons:

* App crashed
* Wrong CMD / ENTRYPOINT
* Port already in use

---

## 🔴 2. Container Exits Immediately

### Inspect exit code

```bash
docker inspect container_id
```

Look for:

```text
"ExitCode": 1
```

### Run container interactively (debug mode)

```bash
docker run -it image_name /bin/bash
```

✅ Helps check if the app starts correctly.

---

## 🔴 3. Image Not Found / Pull Error

### Error:

```text
Unable to find image locally
```

### Fix

```bash
docker pull image_name
```

### Check image exists

```bash
docker images
```

---

## 🔴 4. Port Not Accessible (Website Not Opening)

### Check port mapping

```bash
docker ps
```

Example:

```text
0.0.0.0:8080->80/tcp
```

### Correct way to run

```bash
docker run -p 8080:80 nginx
```

📌 Browser must use **host port (8080)**, not container port.

---

## 🔴 5. “Port Already in Use” Error

### Find which container uses the port

```bash
docker ps
```

### Stop the container

```bash
docker stop container_id
```

Or run on a different port:

```bash
docker run -p 8081:80 nginx
```

---

## 🔴 6. Cannot Enter Container (exec error)

### Error:

```text
container is not running
```

### Fix

```bash
docker start container_id
docker exec -it container_id bash
```

If `bash` is not present:

```bash
docker exec -it container_id sh
```

---

## 🔴 7. Docker Build Failed

### Build with logs

```bash
docker build .
```

### No cache (fresh build)

```bash
docker build --no-cache -t app .
```

📌 Check:

* Dockerfile syntax
* Correct file paths in `COPY`
* Internet access for `RUN apt-get`

---

## 🔴 8. COPY / ADD Not Working in Dockerfile

### Common mistake

```dockerfile
COPY app.py /app/
```

But file is not in the same directory.

### Fix

```bash
ls
```

📌 Docker can only access files **inside the build context**.

---

## 🔴 9. Container Has No Logs

### Try:

```bash
docker logs --tail 50 container_id
```

### Run app in foreground

```bash
docker run image_name
```

📌 App might be logging to a file instead of stdout.

---

## 🔴 10. Disk Space Full (Very Common)

### Check Docker disk usage

```bash
docker system df
```

### Clean unused data

```bash
docker system prune
```

### Full cleanup

```bash
docker system prune -a
```

---

## 🔴 11. Network Issues (Containers Can’t Talk)

### List networks

```bash
docker network ls
```

### Inspect network

```bash
docker network inspect bridge
```

### Run containers in the same network

```bash
docker network create mynet
docker run --network mynet nginx
```

---

## 🔴 12. Volume Data Not Persisting

### Check volumes

```bash
docker volume ls
```

### Inspect volume

```bash
docker volume inspect volume_name
```

### Correct usage

```bash
docker run -v myvolume:/data ubuntu
```

📌 Wrong mount path = data loss.

---

## 🔴 13. Permission Denied Error

### Error:

```text
permission denied
```

### Fix (Linux)

```bash
sudo docker run ...
```

Or add user to docker group:

```bash
sudo usermod -aG docker $USER
```

Logout & login again.

---

## 🔴 14. Docker Daemon Not Running

### Error:

```text
Cannot connect to the Docker daemon
```

### Fix

```bash
sudo systemctl start docker
sudo systemctl status docker
```

---

## 🔴 15. Remove Stuck Containers / Images

### Force remove container

```bash
docker rm -f container_id
```

### Force remove image

```bash
docker rmi -f image_id
```

---

## ⭐ MOST IMPORTANT TROUBLESHOOTING COMMANDS (Interview ⭐)

```bash
docker ps -a
docker logs container
docker inspect container
docker exec -it container bash
docker system df
docker system prune
docker build --no-cache .
```

---

## 🧠 Interview Tip (Very Important)

**When Docker fails, always follow this order:**

1️⃣ `docker ps -a`
2️⃣ `docker logs`
3️⃣ `docker inspect`
4️⃣ Run interactively (`-it`)
5️⃣ Clean system (`prune`)

```
```
