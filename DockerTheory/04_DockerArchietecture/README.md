# 🐳 Docker Architecture – Each Component in Detail

::contentReference[oaicite:0]{index=0}

This document explains **Docker Architecture** in **simple words**, with **proper depth**, suitable for **exams, interviews, and DevOps revision**.

---

## 1️⃣ Docker Client

### 🔹 What is Docker Client?

Docker Client is the **tool used by the user** to communicate with Docker.

It is mainly the **command-line interface (CLI)**.

---

### 🔹 What Docker Client Does

- Takes commands from the user
- Sends requests to Docker Daemon
- Displays output to the user

👉 Docker Client **does not do the actual work**.  
It only **requests** Docker Daemon to perform actions.

---

### 🔹 Examples of Docker Client Commands

- `docker build`
- `docker pull`
- `docker run`
- `docker ps`

---

### 🔹 Important Point

Docker Client can connect to:

- Local Docker Daemon
- Remote Docker Daemon (over network)

---

## 2️⃣ Docker Daemon (dockerd)

### 🔹 What is Docker Daemon?

Docker Daemon is a **background service** that performs **all Docker operations**.

It runs continuously on the Docker Host.

---

### 🔹 What Docker Daemon Does

- Listens for Docker Client requests
- Builds Docker images
- Creates and runs containers
- Manages:
  - Containers
  - Images
  - Networks
  - Volumes

---

### 🔹 Why Docker Daemon is Important

- Without Docker Daemon, Docker cannot work
- It controls and manages all Docker components

👉 Docker Daemon is like a **manager** who does all the work.

---

## 3️⃣ Docker Engine

### 🔹 What is Docker Engine?

Docker Engine is the **core software** that makes Docker work.

It is installed on the host machine.

---

### 🔹 Components of Docker Engine

Docker Engine consists of:

1. Docker Daemon
2. REST API
3. Docker Client

---

### 🔹 Role of Docker Engine

- Accepts Docker commands
- Communicates using REST API
- Runs containers
- Manages Docker objects

👉 Without Docker Engine, **Docker cannot exist**.

---

## 4️⃣ Docker Images

### 🔹 What is a Docker Image?

A Docker Image is a **read-only template** used to create Docker containers.

---

### 🔹 What a Docker Image Contains

- Application code
- Libraries
- Dependencies
- Environment settings
- Instructions to run the application

---

### 🔹 Important Properties of Images

- Images are **immutable** (cannot be changed)
- Images are created using a **Dockerfile**
- Images are built in **layers**

---

### 🔹 Why Docker Images are Important

- Same image runs everywhere
- Same environment for all systems
- Solves “works on my machine” problem

---

## 5️⃣ Docker Containers

### 🔹 What is a Docker Container?

A Docker Container is a **running instance of a Docker Image**.

---

### 🔹 What a Container Does

- Runs the application
- Provides isolation
- Uses host OS kernel
- Starts very fast

---

### 🔹 Container Characteristics

- Lightweight
- Portable
- Can be started, stopped, restarted
- Can be short-lived or long-running

---

### 🔹 Image vs Container Relation

👉 One Image → Many Containers

---

## 6️⃣ Docker Registry

### 🔹 What is Docker Registry?

Docker Registry is a **storage location for Docker images**.

---

### 🔹 Types of Docker Registry

- Public Registry (Docker Hub)
- Private Registry (organization use)

---

### 🔹 What Docker Registry Does

- Stores Docker images
- Allows image upload (push)
- Allows image download (pull)
- Shares images with teams

---

### 🔹 Why Docker Registry is Needed

- To reuse images
- To share applications
- To deploy applications easily

---

## 7️⃣ Dockerfile (Very Important)

### 🔹 What is a Dockerfile?

A Dockerfile is a **text file** that contains instructions to build a Docker image.

---

### 🔹 What a Dockerfile Contains

- Base image
- Application code
- Dependency installation steps
- Command to start application

---

### 🔹 Why Dockerfile is Important

- Automates image creation
- Ensures repeatable builds
- Used in CI/CD pipelines

---

## 8️⃣ Docker Host

### 🔹 What is Docker Host?

Docker Host is the **machine where Docker runs**.

---

### 🔹 What Docker Host Contains

- Docker Engine
- Docker Images
- Docker Containers
- Networks
- Volumes

---

### 🔹 Types of Docker Host

- Local machine
- Virtual machine
- Cloud server

---

## 🔄 Complete Docker Working Flow (Easy)

1. User runs Docker command
2. Docker Client sends request
3. Docker Daemon receives request
4. Docker Daemon:
   - Pulls image from registry OR
   - Builds image using Dockerfile
5. Docker Daemon creates container
6. Application runs inside container

---

## 🧱 Docker Architecture – Text Diagram

```text
User
 ↓
Docker Client
 ↓
Docker Daemon (dockerd)
 ↓
Docker Engine
 ↓
Docker Images
 ↓
Docker Containers
 ↓
Host Operating System
 ↓
Physical Hardware
```

---

## 📝 10-Mark Exam Answer (Perfect)

> Docker architecture follows a client–server model. The Docker Client sends commands to the Docker Daemon, which performs all Docker operations such as building images, running containers, and managing Docker objects. Docker Images are read-only templates created using Dockerfiles, while Docker Containers are running instances of images. Docker Registry stores and shares Docker images. Docker uses OS-level virtualization by sharing the host operating system kernel, which makes containers lightweight and fast.

---

### ✍️ Author

**Ramkumar Prajapati**
Docker • DevOps • Cloud
