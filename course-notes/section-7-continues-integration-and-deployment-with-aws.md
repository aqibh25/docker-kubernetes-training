# Section 7 – Continuous Integration and Deployment with AWS

This section focuses on setting up **CI/CD** for the React Docker project and deploying it to **AWS Elastic Beanstalk** using GitHub Actions.

---

## Workflow Description

The CI/CD workflow is triggered on every **push to the `main` branch**.

It consists of **two jobs**:

1. **Test job** – builds a Docker test image and runs unit tests
2. **Deploy job** – packages the application and deploys it to AWS Elastic Beanstalk (runs only if tests pass)

---

## CI/CD Jobs

### 1. Test Job

- **Runs on**: `ubuntu-latest`
- **Steps**:
   1. Checkout the repository
   2. Build a Docker test image from `Dockerfile.dev`
   3. Run tests inside the Docker container with `npm test`

### 2. Deploy Job

- **Runs on**: `ubuntu-latest`
- **Depends on**: `test` job (deploy runs only if tests pass)
- **Steps**:
   1. Checkout the repository
   2. Generate a deployment package (`deploy.zip`)
   3. Deploy to AWS Elastic Beanstalk
   4. Uses AWS credentials stored in GitHub Secrets

---

## GitHub Actions Workflow

```yaml
name: Deploy Frontend

on:
  push:
    branches: ["main"]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Build Docker test image
        run: docker build -t frontend-test -f Dockerfile.dev .

      - name: Run tests
        run: docker run -e CI=true frontend-test npm test

  deploy:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Generate deployment package
        run: zip -r deploy.zip . -x "*.git*"

      - name: Deploy to Elastic Beanstalk
        uses: einaregilsson/beanstalk-deploy@v21
        with:
          aws_access_key: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws_secret_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          application_name: frontend
          environment_name: Frontend-env
          region: us-east-1
          version_label: ${{ github.sha }}
          deployment_package: deploy.zip
          existing_bucket_name: elasticbeanstalk-us-east-1-622238671061
```
## Project Evidence

As part of this section, a complete **CI/CD pipeline** was implemented for a Dockerized React application.

The project demonstrates:
- Automated testing using **GitHub Actions**
- Building and testing the application inside Docker containers
- Conditional deployment (deploy only if tests pass)
- Deployment to **AWS Elastic Beanstalk**
- Secure handling of AWS credentials using **GitHub Secrets**

The results and supporting evidence for this section are available at:

```
https://github.com/aqibh25/react-docker
```

## Key Takeaways
- CI/CD pipelines help automate testing and deployment workflows
- GitHub Actions can orchestrate multi-step Docker-based pipelines
- Docker ensures consistency between local development, CI, and production
- Deployments should only occur after successful test execution
- AWS Elastic Beanstalk simplifies application deployment and management