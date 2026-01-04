# Section 6 – Creating a Production-Grade Workflow

This section focuses on creating a **production-ready Docker workflow** using a React application.
The goal is to understand how Docker is used differently in **development** versus **production** environments.

---

## Development vs Production Dockerfiles

Instead of using a single Dockerfile, this section introduces **multiple Dockerfiles**:

### Development Dockerfile
- Optimised for rapid development
- Supports live code reloading
- Uses bind mounts so code changes reflect instantly

### Production Dockerfile
- Optimised for performance and security
- Produces a minimal, production-ready image
- Contains only the files needed to run the application

This separation ensures:
- Fast feedback during development
- Small, efficient images in production

---

## Docker Volumes

Docker volumes are a way to store data **outside of a container’s filesystem**.

Key characteristics:
- Data persists even if the container is stopped or deleted
- Managed entirely by Docker
- Not tied directly to a specific directory on the host machine

A helpful way to think about this:
- **Containers are temporary**
- **Volumes are persistent**

Volumes are commonly used for:
- Databases
- Application state
- Dependencies that should not be overwritten

---

## Bind Mounts

Bind mounts map a specific directory on the host machine to a directory inside the container.

Example:

```bash
.:/app
```

Explanation:
- `.` → The current project directory on the host machine
- `/app` → The directory inside the container

With bind mounts:
- Changes made on the host machine instantly appear in the container
- No need to rebuild the image after every code change

Bind mounts are especially useful in development environments.

---

## Volumes vs Bind Mounts

### Bind Mounts
- Directly map a host directory into the container
- Ideal for development
- Changes reflect instantly

### Docker Volumes
- Managed by Docker
- Persist independently of containers
- Ideal for production data and dependencies

Understanding the difference is critical for building efficient Docker workflows.

---

## Project Evidence

As part of this section, a practical project was completed to reinforce the Docker concepts covered.

This project demonstrates:
- A React application running in Docker
- Separate Dockerfiles for development and production
- Use of volumes and bind mounts to improve developer experience


The results and supporting evidence for this section are available at:
```
https://github.com/aqibh25/react-docker
```

---

## Key Takeaways

- Development and production Docker workflows should be separated
- Docker volumes provide persistent storage
- Bind mounts enable fast development with live updates
- Real-world Docker projects often use multiple Dockerfiles
- Proper workflow design improves performance and developer productivity
