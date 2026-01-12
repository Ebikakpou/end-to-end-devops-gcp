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

