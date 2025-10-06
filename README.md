# DevOps Assessment - Next.js Application Deployment

## Project Overview
This project demonstrates my ability to:
- Containerize a Next.js application using Docker
- Automate Docker image build and push with GitHub Actions and GHCR
- Deploy the containerized application to Kubernetes (Minikube)
- Create Kubernetes manifests for Deployment and Service
- Document setup and deployment steps

---

## Table of Contents
1. [Prerequisites](#prerequisites)  
2. [Project Setup](#project-setup)  
3. [Docker](#docker)  
4. [GitHub Actions](#github-actions)  
5. [Kubernetes Deployment](#kubernetes-deployment)  
6. [Accessing the Application](#accessing-the-application)  
7. [File Structure](#file-structure)  
8. [GHCR Image URL](#ghcr-image-url)  

---

## Prerequisites
- Node.js and npm installed  
- Docker installed and running  
- Minikube installed  
- kubectl installed  
- Git and GitHub account  
- Personal Access Token (PAT) with `repo` and `write:packages` scopes for GHCR  

---

## Project Setup

1. Clone the repository:

```bash
git clone https://github.com/Dhanushkumar-Jampana/nextjs-devops-assessment.git
cd nextjs-devops-assessment
Install Next.js dependencies:

npm install
Run the app locally (optional):

npm run dev

2.Docker
Dockerfile
The project includes a Dockerfile for building the Next.js app image.

Build Docker Image

docker build -t ghcr.io/dhanushkumar-jampana/my-nextjs-app:latest .
Push Docker Image to GHCR
Log in to GitHub Container Registry:

echo <YOUR_GHCR_PAT> | docker login ghcr.io -u Dhanushkumar-Jampana --password-stdin
Push the image:

docker push ghcr.io/dhanushkumar-jampana/my-nextjs-app:latest
GitHub Actions
Workflow file: .github/workflows/docker-build.yml

Trigger: Push to main branch

Steps:

Checkout repository

Log in to GHCR

Build Docker image

Tag image with latest and commit SHA

Push image to GHCR

Kubernetes Deployment
Create GHCR Secret (if image is private)
bash
Copy code
kubectl create secret docker-registry ghcr-secret \
  --docker-server=ghcr.io \
  --docker-username=Dhanushkumar-Jampana \
  --docker-password=<YOUR_GHCR_PAT> \
  --docker-email=jampanadhanush7@gmail.com
Deploy Application to Minikube

kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

Verify Pods and Service
kubectl get pods
kubectl get svc

Accessing the Application
Open the app in your browser using Minikube:

minikube service nextjs-service
The terminal will provide a URL similar to:

http://127.0.0.1:63087
⚠️ Keep the terminal open while using the service because Minikube is running a tunnel.

File Structure
my-nextjs-app/
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── .github/
│   └── workflows/
│       └── docker-build.yml
├── Dockerfile
├── package.json
├── pages/
└── README.md

RESULTS:
- Docker Image
<img width="747" height="448" alt="Screenshot 2025-10-07 011705" src="https://github.com/user-attachments/assets/5540cdbe-bda5-4819-b22e-4e865402056a" />



