# Kubernetes Nginx CI/CD Pipeline

A production-style CI/CD pipeline that automatically builds, pushes, and deploys a Dockerized Nginx application to Kubernetes using GitHub Actions.

---

## Project Overview

This project demonstrates an end-to-end DevOps workflow where application changes are automatically built, containerized, and deployed to Kubernetes.

The pipeline performs:

- Code push to GitHub
- Automatic CI/CD trigger
- Docker image build
- Docker Hub image push
- Kubernetes deployment update
- Rolling update of application pods

---

## Architecture


Developer
    |
    | git push
    ↓
GitHub Repository
    |
    ↓
GitHub Actions
    |
    ↓
Self-hosted Runner
    |
    ↓
Docker Build
    |
    ↓
Docker Hub Registry
    |
    ↓
Kubernetes Deployment
    |
    ↓
Running Pods


---

## Technologies Used

- Linux / WSL
- Git
- GitHub
- GitHub Actions
- Docker
- Docker Hub
- Kubernetes
- Minikube
- kubectl

---

# CI/CD Pipeline Flow

## 1. Source Code Management

Developer pushes code changes:

bash
git add .
git commit -m "update application"
git push


GitHub Actions automatically starts the deployment workflow.

---

## 2. Continuous Integration (CI)

The pipeline:

- Checks out source code
- Validates Kubernetes manifests
- Builds Docker image
- Logs into Docker Hub
- Pushes image to Docker Hub

Docker image:


davidonwuka21/nginx-k8s-app:<commit-id>


---

## 3. Continuous Deployment (CD)

After the Docker image is pushed, Kubernetes updates the running application:

bash
kubectl set image deployment/nginx-app


Kubernetes performs a rolling update by replacing old pods with new pods.

---

# Kubernetes Deployment

Application:


Deployment: nginx-app

Replicas: 3

Container:
nginx


Check deployment:

bash
kubectl get deployment


Example:

![Kubernetes Deployment](screenshots/getdeployment.png)

---

## Running Pods

Check running containers:

bash
kubectl get pods


Example:

![Kubernetes Pods](screenshots/getpod.png)

---

# Docker Image

The application is containerized using Docker.

Docker image:


davidonwuka21/nginx-k8s-app


The image is automatically rebuilt and pushed on every GitHub push.

---

# Deployment Strategy

This project uses Kubernetes Rolling Updates.

Benefits:

- Zero downtime deployment
- Automatic pod replacement
- Safer releases
- Versioned container images

---

# CI/CD Pipeline Result

Successful GitHub Actions deployment:

![CI/CD Pipeline Success](screenshots/cicd.png)

---

# Skills Demonstrated

This project demonstrates:

- CI/CD automation
- Docker containerization
- Kubernetes orchestration
- GitHub Actions automation
- Linux administration
- Container deployment
- DevOps workflow design

---

# Future Improvements

Possible improvements:

- Deploy to AWS EKS
- Add Terraform infrastructure
- Add monitoring with Prometheus and Grafana
- Add automated testing
- Add production cloud deployment

---

# Author

David Onwuka

Cloud / DevOps Engineer
