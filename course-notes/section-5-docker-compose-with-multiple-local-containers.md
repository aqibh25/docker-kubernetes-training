# Section 5 – Docker Compose with Multiple Local Containers

This section introduces **Docker Compose**, a tool used to define and run applications that consist of multiple Docker containers.

---

## What Is Docker Compose?

Docker Compose is a Docker tool used to run **multiple containers at the same time**.

- It is installed automatically when Docker is installed
- It allows applications with multiple services to be managed together
- Configuration is defined in a single file: `docker-compose.yml`

---

## Docker CLI vs Docker Compose CLI

### Docker CLI
- Used to run and manage **single containers**
- Containers are started individually using commands like `docker run`

---

### Docker Compose CLI
- Used to define and manage **multi-container applications**
- All services are defined in a single configuration file
- Containers can be started and stopped together

Docker Compose is especially useful when an application depends on multiple services (e.g. a web app and a database).

---

## Docker Compose File Example

Docker Compose uses a file named:

```
docker-compose.yml
```

This file defines:
- The containers that should be created
- How those containers should be configured
- How containers communicate with each other

Example `docker-compose.yml` file:

```yaml
version: "3"

services:
  redis-server:
    image: redis

  node-app:
    build: .
    ports:
      - "4001:8081"
```

---

## Port Mapping

Port mapping allows traffic from the host machine to reach a container.

When using the Docker CLI, ports are mapped using the `-p` flag:

```bash
docker run -p <host-port>:<container-port> <image-name>
```

Example:

```bash
docker run -p 4001:8081 node-app
```

Important notes:
- The host (incoming) port and the container port **do not need to be the same**
- Port mapping allows containerised applications to be accessed through a browser

In Docker Compose, port mappings are defined directly inside the `docker-compose.yml` file.

---

## Container Networking

When Docker Compose is used:
- Docker automatically creates a dedicated network
- All containers defined in the compose file are placed on the same network
- Containers can communicate with each other using their **service names**
- No manual network configuration is required

Simply defining multiple services in a `docker-compose.yml` file is enough for Docker to handle networking.

---

## Running Docker Compose

### Starting Containers

```bash
docker-compose up
```

- Creates and starts all containers defined in the compose file
- Outputs logs from all running containers to the terminal

---

### Running Containers in the Background

```bash
docker-compose up -d
```

- Starts all containers in detached (background) mode
- Frees up the terminal for other commands

---

### Stopping Containers

```bash
docker-compose down
```

- Stops all containers started by Docker Compose
- Removes the containers and the associated Docker network

---

## Restart Policies

Docker Compose allows containers to automatically restart if they crash.

Restart policies are defined inside the service configuration in the `docker-compose.yml` file.

Example:

```yaml
restart: always
```

Available restart options:
- `no` – never restart
- `always` – always restart if stopped
- `on-failure` – restart only if the container exits with an error
- `unless-stopped` – restart unless manually stopped

Restart policies help improve application reliability.

---

## Project Evidence

As part of this section, a practical project was completed to reinforce the Docker concepts covered.

The results and supporting evidence for this section are available at:

`/hands-on/section-5-docker-compose-with-multiple-local-containers`

## Key Takeaways

- Docker Compose is used to manage multi-container applications
- All services are defined in a single configuration file
- Port mapping allows access to containers from the host machine
- Containers are automatically networked together
- Applications can be started and stopped with a single command
- Restart policies improve resilience

