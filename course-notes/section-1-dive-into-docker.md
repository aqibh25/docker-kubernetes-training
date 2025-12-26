# Section 1 – Dive into Docker

## What is Docker?
Docker is a platform and ecosystem for creating, running, and managing containers.  
It allows applications to be packaged together with everything they need to run.

---

## Why Use Docker?
Docker makes it easy to install and run software without worrying about:
- System setup
- Dependency conflicts
- Differences between development and production environments

Applications run the same way regardless of where Docker is installed.

---

## Docker Images
A **Docker image** is:
- A single file that contains all dependencies and configuration required to run a program
- A snapshot of a file system
- Includes a startup command that tells Docker how to run the program

Images are **immutable** and are used as blueprints for containers.

---

## Docker Containers
A **container** is:
- A running instance of an image
- An isolated environment for a program

Containers:
- Do not rely on the host system’s libraries or runtime
- Have their own isolated memory, network, and file system
- Can be started, stopped, moved, and deleted easily

---

## Docker Architecture

### Docker CLI
- The user-facing interface
- Accepts commands (e.g. `docker run`, `docker ps`)
- Sends instructions to the Docker Server (Daemon)

### Docker Server (Docker Daemon)
- Responsible for:
    - Creating images
    - Running containers
    - Managing container lifecycle

### Image Cache
- Stores images that have already been downloaded
- When starting a container:
    1. Docker checks the local image cache
    2. If the image is missing, Docker pulls it from Docker Hub

---

## Linux Features Behind Docker

Docker relies on Linux kernel features to enable containerization.

### Namespacing
- Isolates resources for processes
- Examples:
    - File system
    - Network
    - CPU
    - Process IDs

**Namespacing controls what a process can see.**

### Control Groups (cgroups)
- Limit how much of a resource a process can use
- Examples:
    - CPU usage
    - Memory usage
    - Network bandwidth

**Control groups control how much of a resource a process can use.**

---

## How Docker Runs on Windows

When Docker is installed on Windows:
- A lightweight Linux virtual machine is installed (via WSL2)
- This VM provides a Linux kernel
- All Docker containers run inside this Linux environment

The Linux kernel:
- Hosts container processes
- Manages isolation
- Controls access to system resources

Windows acts as the host, while Docker operates within the Linux VM.

---

## Key Takeaways
- Docker packages applications and dependencies into images
- Containers are isolated runtime instances of images
- Docker relies on Linux kernel features (namespaces and cgroups)
- On Windows, Docker runs inside a Linux virtual machine

---
### Quiz Evidence

Quiz results for this section:  
`/quizzes/section-1-dive-into-docker/section-1-quiz-results.png`