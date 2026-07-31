GitHub Actions CI/CD Pipeline with Docker using Self-Hosted Runner on AWS EC2

A beginner-friendly DevOps project demonstrating how to automate the deployment of a Dockerized web application using GitHub Actions and a Self-Hosted Runner running on an AWS EC2 instance. Every time code is pushed to the main branch, GitHub Actions builds a Docker image, stops the old container, deploys a new container, and makes the latest version of the application available automatically.

Project Architecture
                Developer
                    │
          git add / commit / push
                    │
                    ▼
            GitHub Repository
                    │
                    ▼
          GitHub Actions Workflow
                    │
                    ▼
      Self-Hosted Runner (AWS EC2)
                    │
                    ▼
          Checkout Repository
                    │
                    ▼
          Validate Repository
                    │
                    ▼
           Lint Dockerfile
                    │
                    ▼
       Display Docker Version
                    │
                    ▼
          Build Docker Image
                    │
                    ▼
         List Docker Images
                    │
                    ▼
         Scan Image (Trivy)
                    │
                    ▼
      Stop Existing Container
                    │
                    ▼
     Remove Existing Container
                    │
                    ▼
      Remove Old Docker Image
                    │
                    ▼
       Run New Docker Container
                    │
                    ▼
      Wait for Container Startup
                    │
                    ▼
      Verify Running Container
                    │
                    ▼
          Health Check
                    │
                    ▼
      Display Container Logs
                    │
                    ▼
     Cleanup Docker Resources
                    │
                    ▼
      Deployment Successful
                    │
                    ▼
         Website Available
Technologies Used
Technology	Purpose
Git	Version Control
GitHub	Source Code Repository
GitHub Actions	CI/CD Automation
Self-Hosted Runner	Executes Workflow
Docker	Containerization
Nginx	Web Server
Trivy	Container Image Security Scan
AWS EC2	Deployment Server
Amazon Linux 2023 / Ubuntu	Operating System
Project Structure
Docker/
│
├── .github
│   └── workflows
│       └── main.yml
│
├── Dockerfile
├── index.html
├── sonar-project.properties
├── .gitignore
└── README.md
Prerequisites

Before starting, ensure you have:

AWS Account
EC2 Instance
GitHub Account
Docker Installed
Git Installed
Trivy Installed
GitHub Self-Hosted Runner Configured
EC2 Configuration
Configuration	Value
Instance Type	t2.micro or t3.micro
Operating System	Amazon Linux 2023 / Ubuntu 24.04
Storage	20 GB
Security Group	22, 80, 443
Required Software
Git
Docker
Trivy
GitHub Actions Runner
Workflow Stages

The workflow executes the following stages automatically:

Checkout Source
Validate Repository
Lint Dockerfile
Display Docker Version
Build Docker Image
List Docker Images
Scan Docker Image using Trivy
Stop Existing Container
Remove Existing Container
Remove Old Docker Image
Run Docker Container
Wait for Startup
Verify Running Container
Health Check
Display Container Logs
Cleanup Docker Resources
Deployment Successful
Dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
GitHub Actions Workflow

Workflow Location

.github/workflows/main.yml

Trigger

on:
  push:
    branches:
      - main

Whenever code is pushed to the main branch, GitHub Actions automatically starts the deployment pipeline.

Deployment Process
Developer Push
        │
        ▼
GitHub Repository
        │
        ▼
GitHub Actions
        │
        ▼
Self Hosted Runner
        │
        ▼
Docker Build
        │
        ▼
Docker Deployment
        │
        ▼
Website Updated
Running the Project

Clone Repository

git clone https://github.com/<username>/Docker.git

Go to Project

cd Docker

Build Docker Image

docker build -t website .

Run Docker Container

docker run -d --name website -p 80:80 website

Verify

docker ps

Open Browser

http://EC2_PUBLIC_IP
Useful Docker Commands

Build Image

docker build -t website .

Run Container

docker run -d --name website -p 80:80 website

Stop Container

docker stop website

Remove Container

docker rm website

List Images

docker images

List Containers

docker ps

Container Logs

docker logs website
Expected GitHub Actions Output
✔ Setup job
✔ Checkout Source
✔ Validate Repository
✔ Lint Dockerfile
✔ Display Docker Version
✔ Build Docker Image
✔ List Docker Images
✔ Scan Docker Image
✔ Stop Existing Container
✔ Remove Existing Container
✔ Remove Old Docker Image
✔ Run Docker Container
✔ Wait for Startup
✔ Verify Running Container
✔ Health Check
✔ Display Container Logs
✔ Cleanup Docker Resources
✔ Deployment Successful
✔ Complete Job
Project Features
Automated CI/CD Pipeline
Docker Container Deployment
GitHub Actions Automation
Self-Hosted Runner
Docker Image Security Scanning
Automatic Website Deployment
Health Check Validation
Container Log Verification
Automatic Cleanup
Easy to Extend
