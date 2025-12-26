# Section 4 – Making a Real Project with Docker

This section applies the Docker concepts learned so far by building and running a real Node.js application inside a 
container.
---

## Node.js Application

A simple Node.js web application is created for this section.

Every Dockerfile typically follows this structure:
- Specify a base image
- Run commands to install dependencies
- Specify a command to run when the container starts

---

## Using Docker for the Project

Docker is used to:

- Define the runtime environment for Node.js
- Install required dependencies
- Run the web application inside a container

This approach ensures:
- Consistent behavior across environments
- No dependency conflicts on the host system
- Easy setup and repeatable builds

---

## Accessing the Application in the Browser

Once the container is running:

- The application exposes a network port
- Requests from the host machine are forwarded to the container
- The application can be accessed via a web browser

This confirms that the containerised Node.js app is running correctly.

---

## Project Location

The files for this hands-on project can be found in the following directory:

`/hands-on/section-4-making-real-projects-with-docker/`


This directory contains:
- The Node.js application source code
- Docker configuration files
- Package.json

---


## Key Takeaways

- Docker can be used to containerise real applications
- Node.js applications run reliably inside containers
- Containers simplify environment setup and consistency
- Applications inside containers can be accessed through a browser

---

### Quiz Evidence

Quiz results for this section are available here:  
`/quizzes/section-4-making-real-projects-with-docker/`
"""