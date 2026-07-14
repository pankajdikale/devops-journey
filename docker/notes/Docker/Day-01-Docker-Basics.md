# 🐳 Docker Day 01 - Docker Basics & Project Deployment

> **Course:** 90 Days of DevOps (Udaan Batch)
> **Project:** DevBoard + EduSnap
> **Author:** Pankaj Dikale
> **Status:** ✅ Completed

---

# 🎯 Learning Objectives

By the end of this session, I should be able to:

- Explain what Docker is.
- Explain why Docker was created.
- Differentiate between Virtual Machines and Containers.
- Understand Docker Architecture.
- Run Docker containers.
- Build Docker images.
- Deploy a simple Flask application.
- Build the DevBoard frontend using Docker.

---

# 🤔 Why Docker?

Before Docker, developers installed all dependencies directly on their operating systems.

Example:

- Python
- Node.js
- PostgreSQL
- Java
- Nginx

Different versions often caused the famous problem:

> **"It works on my machine."**

Docker solves this problem by packaging the application along with all its dependencies into a portable **Image**.

That image can run anywhere Docker is installed.

---

# 🧠 What is Docker?

Docker is a **Containerization Platform**.

It packages:

- Application Code
- Runtime
- Libraries
- Dependencies
- Environment Variables

inside an Image.

That Image can be executed as a **Container**.

---

# 💡 Virtual Machine vs Container

| Virtual Machine | Docker Container |
|-----------------|------------------|
| Includes Guest OS | Shares Host OS Kernel |
| Heavy | Lightweight |
| Slow Startup | Fast Startup |
| Uses More RAM | Uses Less RAM |
| Large Storage | Small Image Size |

---

# 🏗 Docker Architecture

```text
                Docker Hub
                     ▲
                     │
          Pull       │      Push
                     │
Docker Client ─────────────► Docker Daemon
      │                        │
      │                        │
      ▼                        ▼
 Docker Images           Docker Containers
```

---

## Components

### Docker Client

CLI used by developers.

Example

```bash
docker build
docker run
docker ps
```

---

### Docker Daemon

Background service responsible for

- Building Images
- Running Containers
- Managing Networks
- Managing Volumes

---

### Docker Image

Blueprint of an application.

Think of it like a **Class** in Object Oriented Programming.

---

### Docker Container

Running instance of an Image.

Think of it as an **Object**.

---

### Docker Registry

Stores Images.

Example:

- Docker Hub

---

# 📚 Docker Workflow

```text
Dockerfile
      │
      ▼
docker build
      │
      ▼
Docker Image
      │
      ▼
docker run
      │
      ▼
Docker Container
```

---

# 💻 Commands

## docker images

### What?

Lists all downloaded Docker Images.

### Why?

Used to verify available Images.

---

## docker ps

### What?

Shows currently running Containers.

---

## docker ps -a

### What?

Shows all Containers including stopped Containers.

---

## docker run nginx

### What?

Downloads (if needed) and starts an Nginx container.

---

## docker run -d nginx

### What?

Runs container in detached mode.

### Breakdown

```text
-d

Detached Mode

Runs in background.
```

---

## docker run -p 80:80 nginx

### What?

Maps

Host Port → Container Port

```text
localhost:80

↓

Docker

↓

Nginx Container :80
```

### Why?

Without Port Mapping

Application runs

BUT

Cannot be accessed from Browser.

---

## docker run -it ubuntu bash

### Breakdown

```text
-i

Interactive Mode

-t

Allocate Terminal

bash

Start Bash Shell
```

### Why?

Allows us to work inside Ubuntu Container.

---

# 🧪 Practical Work

Completed:

- Nginx Container
- Ubuntu Container
- Flask Dockerization
- DevBoard Frontend Dockerization

---

# 🔥 Best Practices

- Use Official Images
- Keep Images Small
- Remove Unnecessary Files
- Use Multi-stage Builds
- Don't run everything as Root
- Tag Images Properly

---

# ⚠️ Common Mistakes

❌ Forgetting Port Mapping

Result:

Application cannot be accessed.

---

❌ Confusing Image with Container

Remember

Image

↓

Blueprint

Container

↓

Running Application

---

❌ Forgetting Detached Mode

Container blocks terminal.

---

# 🚀 EduSnap Connection

How Docker is used in EduSnap

- Dockerized FastAPI Backend
- Dockerized React Frontend
- PostgreSQL Container
- Docker Compose manages all three services

Architecture

```text
Browser

↓

Frontend

↓

Backend

↓

PostgreSQL
```

---

# 🎤 Interview Questions

## Q1. What is Docker?

### Answer

Docker is a containerization platform that packages an application along with its dependencies into an Image, allowing it to run consistently across different environments.

---

## Q2. Why do we use Docker?

### Answer

Docker eliminates environment-related issues ("It works on my machine"), improves portability, simplifies deployment, and isolates applications.

---

## Q3. Difference between Image and Container?

### Answer

| Image | Container |
|--------|-----------|
| Blueprint | Running Instance |
| Read-only | Read-Write |
| Static | Running Process |

---

## Q4. Difference between Docker and Virtual Machine?

### Answer

Docker shares the Host OS Kernel and is lightweight.

Virtual Machines include a complete Guest Operating System, making them heavier.

---

## Q5. What happens when you run docker run nginx?

### Answer

Docker checks if the nginx Image exists locally.

If not

↓

Downloads Image from Docker Hub

↓

Creates Container

↓

Starts Container

---

## Q6. Difference between docker ps and docker ps -a?

### Answer

docker ps

Shows Running Containers.

docker ps -a

Shows All Containers.

---

## Q7. Why do we use -d?

### Answer

Runs Container in Detached Mode (Background).

---

## Q8. Why do we use -it?

### Answer

Allows interactive terminal access inside the Container.

---

## Q9. Why do we use -p?

### Answer

Maps Host Port to Container Port so applications inside Containers are accessible from outside.

---

## Q10. Explain Docker Architecture.

### Answer

Docker Client sends commands to Docker Daemon.

Docker Daemon builds Images, runs Containers, and communicates with Docker Registry for pulling and pushing Images.

---

# 📝 Revision Questions

- What is Docker?
- Why Docker?
- Difference between Image and Container?
- Difference between VM and Container?
- Explain Docker Architecture.
- Explain Docker Workflow.
- Explain docker run.
- Explain docker build.
- Explain docker ps.
- Explain Port Mapping.
- Explain Detached Mode.
- Explain Interactive Mode.

---

# ⭐ Key Takeaways

- Docker packages applications with dependencies.
- Images are Blueprints.
- Containers are Running Instances.
- Docker improves portability.
- Containers are lightweight.
- Practice is more important than memorizing commands.
- Always connect new concepts with EduSnap.

---

# 📌 My Learnings

- Docker solves environment inconsistency.
- Understanding "Why" is more important than remembering commands.
- Docker became much easier after reverse engineering my own EduSnap project.
