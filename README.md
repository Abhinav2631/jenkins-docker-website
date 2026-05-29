# CI/CD Automated Website Deployment using Jenkins, Docker, GitHub, and AWS EC2 on Netflix Clone

## Project Overview

This project demonstrates the implementation of a Continuous Integration and Continuous Deployment (CI/CD) pipeline for deploying a Netflix Clone website using GitHub, Jenkins, Docker, and AWS EC2. The objective of the project is to automate the deployment process so that any changes pushed to the GitHub repository can be automatically built and deployed through Jenkins.

The project uses GitHub as the source code repository, Jenkins as the automation server, Docker for containerization, and AWS EC2 as the cloud hosting platform. The website is deployed inside a Docker container and made accessible through the public IP address of the EC2 instance.

---

## Technologies Used

* AWS EC2
* GitHub
* Jenkins
* Docker
* Java 21
* Amazon Linux 2023
* HTML
* CSS
* JavaScript
* SSH

---

## Project Architecture

```text
Developer
    ↓
GitHub Repository
    ↓
Jenkins Pipeline
    ↓
Docker Build
    ↓
Docker Container
    ↓
AWS EC2 Server
    ↓
Live Netflix Clone Website
```

---

# Day 1 – AWS & Jenkins Setup

### Tasks Performed

* Launched Jenkins EC2 Instance on AWS
* Configured Security Groups
* Connected to EC2 using EC2 Instance Connect
* Updated system packages
* Installed Java 21
* Installed Jenkins
* Started and enabled Jenkins service
* Installed Git
* Installed Docker
* Configured Jenkins Dashboard
* Created Jenkins Administrator Account
* Installed recommended Jenkins plugins

### Outcome

The Jenkins server was successfully configured and became fully operational for CI/CD automation.

---

# Day 2 – GitHub & Web Server Setup

### Tasks Performed

* Created GitHub repository named **netflix-clone-cicd**
* Developed Netflix Clone website files
* Created:

  * index.html
  * style.css
  * script.js
  * Dockerfile
* Updated README.md
* Created Web Server EC2 Instance
* Installed Apache Web Server
* Configured HTTP and SSH access
* Verified Apache service status
* Verified website accessibility

### Outcome

GitHub repository and AWS Web Server were configured successfully.

---

# Day 3 – Jenkins Integration & SSH Configuration

### Tasks Performed

* Generated SSH key pair on Jenkins Server
* Configured passwordless SSH authentication
* Added Jenkins public key to Web Server
* Verified SSH connectivity between Jenkins Server and Web Server
* Connected Jenkins with GitHub repository
* Created Jenkins Pipeline Job
* Configured Pipeline stages
* Added deployment commands

### Outcome

Jenkins successfully integrated with GitHub and established secure passwordless communication with the Web Server.

---

# Day 4 – Automation & CI/CD Testing

### Tasks Performed

* Configured GitHub Webhook
* Configured Jenkins Build Trigger
* Connected GitHub webhook with Jenkins
* Automated build triggering process
* Tested CI/CD workflow
* Pushed code updates to GitHub
* Verified automatic Jenkins build execution
* Verified Docker image creation
* Verified automatic deployment process

### Outcome

The CI/CD pipeline successfully automated the build and deployment process using GitHub, Jenkins, Docker, and AWS EC2.

---

# Day 5 – Documentation & Final Verification

### Tasks Performed

* Verified successful Jenkins Pipeline execution
* Verified Docker container status
* Verified Jenkins Build History
* Verified Console Output
* Verified Netflix Clone deployment
* Captured project screenshots
* Prepared project documentation
* Performed final testing

### Outcome

The project was successfully completed and became ready for submission.

---

# Jenkins Pipeline Workflow

The Jenkins Pipeline performs the following tasks automatically:

### Stage 1 – Clone Repository

* Jenkins connects to GitHub.
* Retrieves the latest source code from the repository.

### Stage 2 – Build Docker Image

* Jenkins executes Docker build commands.
* Creates a Docker image named:

```text
netflix-clone
```

### Stage 3 – Run Docker Container

* Stops any previously running container.
* Removes old containers.
* Creates and starts a new Docker container.

### Stage 4 – Deployment Verification

* Verifies successful container execution.
* Hosts the Netflix Clone website on AWS EC2.

---

# Docker Configuration

### Dockerfile

```dockerfile
FROM nginx:latest

COPY . /usr/share/nginx/html

EXPOSE 80
```

### Docker Commands Used

```bash
docker build -t netflix-clone .
docker run -d -p 80:80 --name netflix-container netflix-clone
docker ps
```

---

# Jenkins Pipeline Script

```groovy
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Abhinav2631/netflix-clone-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t netflix-clone .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop netflix-container || true
                docker rm netflix-container || true
                docker run -d -p 80:80 --name netflix-container netflix-clone
                '''
            }
        }
    }
}
```

---

# Results and Outcome

The Netflix Clone website was successfully deployed using a Jenkins Pipeline integrated with GitHub, Docker, and AWS EC2.

The project successfully demonstrated:

* Continuous Integration and Continuous Deployment (CI/CD)
* GitHub Integration
* Jenkins Pipeline Automation
* Docker Containerization
* AWS EC2 Deployment
* Passwordless SSH Authentication
* Automated Website Deployment

---

# Screenshots Included

1. Jenkins EC2 Instance
2. Security Group Configuration
3. Java Installation
4. Git Installation
5. Docker Installation
6. GitHub Repository
7. Jenkins Dashboard
8. Jenkins Pipeline Configuration
9. Jenkins Stage View
10. Jenkins Successful Build
11. Jenkins Console Output
12. SSH Authentication Success
13. Docker Container Running
14. Netflix Clone Website Output

---

# Conclusion

This project provided practical experience in implementing a complete DevOps CI/CD workflow using GitHub, Jenkins, Docker, and AWS EC2. Through automation and containerization, website deployment was simplified and made more efficient. The project enhanced practical knowledge of cloud computing, continuous integration, continuous deployment, containerization, and infrastructure automation, which are essential skills in modern DevOps engineering.
