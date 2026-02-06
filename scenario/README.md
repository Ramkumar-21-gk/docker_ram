
# 🐳 Docker Scenario-Based Interview Questions & Answers

This document contains **scenario-based Docker interview questions with clear thinking and commands**, written in **easy English** and **practical style**, exactly how interviewers expect answers.

---

## 🔹 Scenario 1: Container stops immediately after starting

### ❓ Problem
You run a container, but it exits instantly.

### 🧠 Reason
- Main process finished  
- App crashed  
- Wrong CMD / ENTRYPOINT  

### ✅ Troubleshooting Steps

```bash
docker ps -a
docker logs container_id
````

### ✅ Fix

```bash
docker run -it image_name /bin/bash
```

Explain in interview:

> “A container runs only while its main process is alive.”

---

## 🔹 Scenario 2: Website not opening on browser

### ❓ Problem

Container is running, but browser shows **site can’t be reached**.

### 🧠 Reason

* Port not exposed
* Wrong port mapping

### ✅ Check

```bash
docker ps
```

### ✅ Fix

```bash
docker run -p 8080:80 nginx
```

Explain:

> “Browser uses host port, not container port.”

---

## 🔹 Scenario 3: “Port already in use” error

### ❓ Problem

```text
bind: address already in use
```

### 🧠 Reason

Another container or app already uses that port.

### ✅ Check

```bash
docker ps
```

### ✅ Fix

```bash
docker stop container_id
```

OR

```bash
docker run -p 8081:80 nginx
```

---

## 🔹 Scenario 4: Cannot enter container using docker exec

### ❓ Problem

```text
container is not running
```

### 🧠 Reason

Container is stopped.

### ✅ Fix

```bash
docker start container_id
docker exec -it container_id bash
```

If `bash` is not available:

```bash
docker exec -it container_id sh
```

---

## 🔹 Scenario 5: Docker image build fails

### ❓ Problem

`docker build` fails.

### 🧠 Reason

* Dockerfile syntax error
* Wrong file path in COPY
* Internet issue

### ✅ Debug

```bash
docker build --no-cache .
```

Explain:

> “No-cache helps identify the exact failing layer.”

---

## 🔹 Scenario 6: COPY command not working in Dockerfile

### ❓ Problem

Build succeeds but file missing inside container.

### 🧠 Reason

File not in build context.

### ✅ Fix

```bash
ls
docker build .
```

Explain:

> “Docker can only copy files inside the build directory.”

---

## 🔹 Scenario 7: Logs are empty

### ❓ Problem

`docker logs` shows nothing.

### 🧠 Reason

App writes logs to a file instead of stdout.

### ✅ Fix

```bash
docker exec -it container_id bash
```

Explain:

> “Docker captures only stdout and stderr.”

---

## 🔹 Scenario 8: Containers cannot communicate with each other

### ❓ Problem

One container can’t reach another.

### 🧠 Reason

Containers are on different networks.

### ✅ Fix

```bash
docker network create mynet
docker run --network mynet app1
docker run --network mynet app2
```

Explain:

> “Containers must be on the same network.”

---

## 🔹 Scenario 9: Data lost after container restart

### ❓ Problem

Data disappears when container stops.

### 🧠 Reason

No volume attached.

### ✅ Fix

```bash
docker volume create myvol
docker run -v myvol:/data app
```

Explain:

> “Volumes persist data beyond container lifecycle.”

---

## 🔹 Scenario 10: Docker daemon not running

### ❓ Problem

```text
Cannot connect to the Docker daemon
```

### 🧠 Reason

Docker service stopped.

### ✅ Fix

```bash
sudo systemctl start docker
sudo systemctl status docker
```

---

## 🔹 Scenario 11: Disk space full due to Docker

### ❓ Problem

System storage full.

### 🧠 Reason

Unused images and containers.

### ✅ Fix

```bash
docker system df
docker system prune -a
```

Explain:

> “Prune removes unused Docker objects.”

---

## 🔹 Scenario 12: Permission denied while running Docker

### ❓ Problem

```text
permission denied
```

### 🧠 Reason

User not in docker group.

### ✅ Fix

```bash
sudo usermod -aG docker $USER
```

Logout and login again.

---

## 🔹 Scenario 13: Image pulls slowly or fails

### ❓ Problem

`docker pull` is very slow.

### 🧠 Reason

Network or registry issue.

### ✅ Fix

```bash
docker pull nginx:latest
```

Explain:

> “Docker pulls images layer by layer.”

---

## ⭐ MOST IMPORTANT INTERVIEW LINE

> “Whenever Docker fails, I check container status, logs, inspect details, and then debug interactively.”

---

## ⭐ MUST-REMEMBER COMMANDS (Interview)

```bash
docker ps -a
docker logs container
docker inspect container
docker exec -it container bash
docker system prune
docker build --no-cache .
```

```
```
