# Section 2 – Manipulating Containers with the Docker Client

This section focuses on using the Docker client (CLI) to create, run, inspect, and manage containers.

---

## Running Containers

The main command used to create and run containers is:

- `docker run <image-name>`

This command:
- Creates a container from an image
- Runs the image’s default startup command

You can override the default command by providing your own:

- `docker run <image-name> <command>`

Example:

- `docker run busybox echo hi there`

This prints `hi there` to the terminal.

---

## Commands Inside Containers

Commands only work if they exist **inside the container’s file system**.

For example:
- `busybox` contains basic Linux utilities like `echo` and `ls`
- `hello-world` does not

Running the following will fail:

- `docker run hello-world echo hi there`

This happens because the `echo` command does not exist in the `hello-world` image.

---

## Listing Containers

Docker provides commands to inspect container state:

- `docker ps`  
  Shows currently running containers

- `docker ps --all`  
  Shows all containers, including stopped ones

---

## Docker Run vs Create vs Start

Although commonly used, `docker run` is actually a combination of two commands.

### docker create
- Creates a container
- Sets up the file system
- Does **not** start the container

### docker start
- Starts an existing container
- Uses the container’s startup command

You can attach output to your terminal using:
- `docker start -a <container-id>`

If the startup command was overridden when the container was created, Docker will reuse that command on every restart.

---

## Container Lifecycle Management

### Removing Unused Resources
- `docker system prune` removes:
    - Stopped containers
    - Unused Docker resources

### Viewing Logs
- `docker logs <container-id>` retrieves:
    - All logs from a container
    - Even after the container has stopped

This command does **not** restart the container.

---

## Stopping Containers

There are two ways to stop a container:

### docker stop
- Sends a **SIGTERM** signal
- Allows the container to shut down gracefully
- Docker waits about 10 seconds before forcing termination

### docker kill
- Sends a **SIGKILL** signal
- Immediately stops the container
- No cleanup is performed

**Best practice:**  
Use `docker stop` first and only use `docker kill` if the container is unresponsive.

---

## Executing Commands in a Running Container

Docker allows you to run additional commands inside an already running container.

- `docker exec -it <container-id> <command>`

Flags:
- `-i` connects your terminal to STDIN
- `-t` allocates a terminal (TTY)

Example:
- `docker exec -it <container-id> sh`

This opens a shell inside the container.

---

## STDIO Streams in Containers

Every running process has three communication streams:

- **STDIN** – standard input
- **STDOUT** – standard output
- **STDERR** – standard error

The `-it` flags allow your terminal to interact with these streams.

---

## Container Isolation

By default:
- Containers are fully isolated
- File systems are not shared between containers
- Containers created from the same image run independently

---

## Key Takeaways

- `docker run` creates and starts containers
- Commands must exist inside the container image
- Containers can be listed, logged, stopped, and restarted
- Graceful shutdown is preferred over forced termination
- Containers are isolated by default

---

### Quiz Evidence

Quiz results for this section are available here:  
`/quizzes/01-dive-into-docker/`

