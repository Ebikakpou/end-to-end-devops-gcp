# End-to-End DevOps Project on GCP

## Overview
This project demonstrates a complete DevOps workflow: building, containerizing, deploying, and monitoring an application on Google Cloud Platform (GCP).

## Technologies Used
- Google Cloud Platform (Compute Engine)
- Docker
- GitHub Actions
- Terraform
- Nginx
- Prometheus & Grafana
- Linux (Ubuntu)

## Project Goal
To automate application delivery from code to production using industry-standard DevOps tools and practices.

## Application Design

### Node.js + Express
We use Node.js as our backend runtime and Express.js as the web framework. This allows us to quickly build and expose HTTP endpoints.

### Endpoints
- `/` : Returns a welcome message
- `/health` : Returns status and version for monitoring and health checks

### Why Health Checks Matter
Health endpoints allow automated systems (like CI/CD pipelines, Prometheus, or Nginx) to check if the app is running correctly. They are essential for observability and reliability in production systems.


## Containerization with Docker

### Why Docker?
Docker allows us to package the application, runtime, and dependencies into a single portable unit. This ensures the application runs consistently across development, CI/CD pipelines, and cloud environments.

### Docker Image Design
- Uses official `node:18-alpine` image for small size and security
- Separates dependency installation from source code for faster builds
- Exposes port `3000` for HTTP traffic

### Health Checks
A Docker health check is configured to periodically call the `/health` endpoint. This allows container platforms to detect unhealthy containers and restart them automatically.

### Benefits for DevOps
- Predictable deployments
- Easy scaling
- Seamless CI/CD integration
- Foundation for Kubernetes

## Cloud Infrastructure on GCP

### Why Google Cloud Platform (GCP)?
GCP provides reliable, scalable cloud infrastructure and integrates well with containerized workloads. It is widely used in modern DevOps environments.

### GCP Project Structure
All resources are created within a dedicated GCP project. This provides isolation, billing control, and centralized IAM management.

### Compute Engine
We use a Google Compute Engine virtual machine running Ubuntu Linux to host the containerized application.

### VM Responsibilities
- Run Docker containers
- Host Nginx reverse proxy
- Serve as deployment target for CI/CD pipelines

## Cloud Infrastructure on GCP

### Why Google Cloud Platform (GCP)?
GCP provides reliable, scalable cloud infrastructure and integrates well with containerized workloads. It is widely used in modern DevOps environments.

### GCP Project Structure
All resources are created within a dedicated GCP project. This provides isolation, billing control, and centralized IAM management.

### Compute Engine
We use a Google Compute Engine virtual machine running Ubuntu Linux to host the containerized application.

### VM Responsibilities
- Run Docker containers
- Host Nginx reverse proxy
- Serve as deployment target for CI/CD pipelines

## Infrastructure as Code with Terraform

### Why Terraform?
Terraform allows us to define cloud infrastructure using code. This makes infrastructure reproducible, version-controlled, and reviewable.

### Managed Resources
- Google Compute Engine VM
- Firewall rules for HTTP traffic

### Terraform Workflow
1. `terraform init` – initialize provider
2. `terraform plan` – preview infrastructure changes
3. `terraform apply` – provision infrastructure
4. `terraform destroy` – remove infrastructure safely

### Benefits
- No manual cloud configuration
- Consistent environments
- Easy teardown and recreation
