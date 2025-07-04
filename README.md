# Full Stack Deployment with ArgoCD, Jenkins, and Kubernetes

This repository includes all required Kubernetes manifests and configuration files fully automated deployment and continuous updates of all services. All files are managed via **ArgoCD**, while the Docker images are built and injected into the manifests by a **Jenkins pipeline** located in a **separate repository**.


## Repository Structure:

- `spring-backend/`
  - `spring-deployment.yaml`: Spring deployment
  - `spring-mvc.yaml`: Service backend
  - `spring-ingress.yaml`: Ingress backend

- `vue-frontend/`
  - `vue-deployment.yaml`: Vue.js frontend deployment
  - `vue-svc.yaml`: Service frontend
  - `vue-ingress.yaml`: Ingress frontend

- `postsgres/`
  - `postsgres-deployment.yaml`: Deployment that use PVC to store posts
  - `postsgres-service.yaml`: Service
  - `postsgres-pvc.yaml`: Persistent Volume Claim

---

## Requirements

- ArgoCD must be install in Kubernetes cluster.
- Jenkins server with ssh acess to this repository.
- A shared image registry for the images (e.g. DockerHub, GitLab Container Registry, etc.)

## How images updates
Jenkins user connects to this repository via SSH
   - **Replaces only the `tag`** in the `image:` fields of the relevant `deployment.yaml` files
        image:ghcr.io/nikos-kaparos/crowdfunding-backend:3215aa8-104, after jenkins pipeline
        then tag 3215aa8-104 will be change.


