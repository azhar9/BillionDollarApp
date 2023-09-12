# BillionDollarApp

Welcome to `billiondollarapp` - the next big thing in the tech world. This README will guide you through setting up a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins. We'll also give you a primer on Docker, Jenkins, and the basics of CI/CD.

## Prerequisites

- A basic understanding of Git & GitHub.
- Docker installed on your machine. If not, follow [Docker's official guide](https://docs.docker.com/get-docker/).
- Jenkins installed on your machine. Refer to the [Jenkins installation guide](https://www.jenkins.io/doc/book/installing/).

## Table of Contents

1. [Introduction to Docker](#introduction-to-docker)
2. [Introduction to Jenkins](#introduction-to-jenkins)
3. [Basics of CI/CD](#basics-of-cicd)
4. [Setting up a Jenkins CI/CD Pipeline](#setting-up-a-jenkins-cicd-pipeline)

## Introduction to Docker

**Docker** is a platform that allows you to develop, ship, and run applications inside containers. Think of containers as lightweight, standalone executable software packages that encompass everything an app needs to run, ensuring consistent behavior across environments.

**Key Terms:**
- **Image:** A snapshot of a container. It’s a lightweight, stand-alone, executable software package.
- **Container:** A running instance of an image.
  
**Basic Docker Commands:**

```bash
# Pull an image from DockerHub
docker pull <image_name>
# List all running containers
docker ps
# Run a container
docker run <image_name>
# Stop a container
docker stop <container_id>
```
## Introduction to Jenkins

**Jenkins** is an open-source automation tool to facilitate CI/CD. With Jenkins, teams can automate various stages of the development process.

### Key Concepts:
- **Pipeline:** A series of automated processes to get code from version control straight to your users.
- **Executor:** A computational resource where builds can be run.
- **Node:** A machine on which Jenkins runs.

## Basics of CI/CD

- **Continuous Integration (CI):** A software development practice where developers integrate code into a shared repository frequently. Automated tests validate these integrations.
  
- **Continuous Deployment (CD):** The process of automatically deploying the integrated code to production after passing CI tests.

## Setting up a Jenkins CI/CD Pipeline

   - Setup Jenkins Using the provided docker commands
      ```bash
      docker build -t jenkins-server -f ./Dockerfile_jenkins_server .
      ```
   - To run our Jenkins Docker image, use the following command:
      ```bash
        docker run --name jenkins -d -v jenkins_home:/var/jenkins_home -p 8080:8080 -p 50000:50000 --restart=on-failure jenkins-server
      ```
   - Open your browser and navigate to [http://localhost:8080/](http://localhost:8080/) to access the Jenkins dashboard.
   - Complete the initial setup.

### 2. Create a New Jenkins Job
   - On the Jenkins dashboard, click on `New Item`.
   - Enter a name for your job, select `Freestyle project`, and click `OK`.

### 3. Configure Source Code Management
   - Under `Source Code Management`, select `Git`.
   - Enter your GitHub repository URL.

### 4. Configure Build Triggers
   - Check `Poll SCM` and set a schedule. For instance, `H/5 * * * *` will poll the repository every 5 minutes.

### 5. Add Build Steps
   - Click on `Add build step` and select `Execute shell`.
   - Add commands to build your project (e.g., `docker build -t billiondollarapp .`).

### 6. Add Post-build Actions for Deployment
   - Click on `Add post-build action`.
   - Configure according to your deployment environment.

### 7. Save and Build
   - Click on `Save`.
   - Click on `Build Now` to start the CI/CD process.

**Congratulations!** You've now set up a basic Jenkins CI/CD pipeline for your `billiondollarapp`.

## Feedback & Contributions

Feel free to raise issues or submit Pull Requests on GitHub. All contributions are welcome.
