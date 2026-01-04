# Section 8 – Building a Multi-Container Application

This section focuses on building and deploying a **multi-container application** using Docker, CI/CD, and AWS.

---

## Application Architecture

The application is split into multiple services, each running in its own container:

### Frontend (React)
- Provides the user interface
- Communicates with the backend API
- Built and served from a Docker image

### Backend (Express.js)
- Handles API requests from the frontend
- Communicates with the PostgreSQL database
- Runs as a separate Docker container

### Database (PostgreSQL)
- Acts as the persistence layer
- Runs in its own container
- Stores application data independently of the frontend and backend

Each service is isolated but connected through Docker networking.

---

## Dockerization Strategy

- Each service has its own **Dockerfile**
- Services are configured to communicate using container names
- Environment variables are used to manage configuration
- Docker ensures consistency across:
    - Local development
    - CI environment
    - Production deployment

---

## CI/CD Workflow

A CI/CD pipeline is implemented using **GitHub Actions**:

1. Code is pushed to GitHub
2. GitHub Actions pipeline is triggered
3. Application is tested and built using Docker
4. Docker images are built for each service
5. Images are pushed to **Docker Hub**
6. AWS Elastic Beanstalk pulls the images
7. Application is deployed automatically

This workflow ensures reliable and repeatable deployments.

---

## Deployment Strategy

- Docker images are stored in **Docker Hub**
- AWS Elastic Beanstalk is configured to pull the required images
- The application is deployed as a multi-container environment
- Updates are deployed automatically after successful CI runs

---

## Project Evidence

As part of this section, a complete **multi-container full-stack application** was implemented.

The project demonstrates:
- Dockerizing frontend, backend, and database services
- Inter-container communication
- CI/CD automation using GitHub Actions
- Image publishing to Docker Hub
- Deployment to AWS Elastic Beanstalk

The full project can be found here:
```
https://github.com/aqibh25/multi-react-docker
```

## Key Takeaways
- Multi-container applications allow services to scale independently
- Docker simplifies service isolation and communication
- CI/CD pipelines automate testing, building, and deployment
- Docker Hub acts as a central image registry
- AWS Elastic Beanstalk can deploy complex containerized applications