# CI/CD Pipeline with GitHub Actions and Kind

This repository demonstrates the implementation of a CI/CD pipeline using GitHub Actions to set up a local Kubernetes cluster with [Kind](https://kind.sigs.k8s.io/), build and deploy a Docker application, and perform basic testing.

## Features

- Installs necessary dependencies (`docker`, `kubectl`, `kind`).
- Creates a Kubernetes cluster using Kind.
- Builds a Docker image for the application.
- Deploys the application to the cluster.
- Performs readiness checks and basic debugging.
- Tests the application via `curl`.

## Workflow Overview

The GitHub Actions workflow file (`.github/workflows/main.yml`) automates the following steps:

1. **Dependency Installation**: Installs Docker, kubectl, and Kind.
2. **Cluster Setup**: Creates a Kind cluster named `ci-cd-cluster`.
3. **Docker Build and Load**: Builds the application image and loads it into the Kind cluster.
4. **Deployment**: Applies Kubernetes manifests (`k8s/deployment.yaml`, `k8s/service.yaml`) to deploy the application.
5. **Testing**: Verifies pod readiness and tests the application via port forwarding.

## Prerequisites

Before using this repository:

- Configure the following GitHub Secrets for Docker Hub authentication:
  - `DOCKER_USERNAME`: Your Docker Hub username.
  - `DOCKER_PASSWORD`: Your Docker Hub password.

## Folder Structure

```
.
├── .github/
│   └── workflows/
│       └── main.yml   # GitHub Actions workflow file
├── app/
│   ├── Dockerfile      # Dockerfile for the application
│   └── app.py            # Application source code
├── k8s/
│   ├── deployment.yaml # Kubernetes Deployment manifest
│   ├── service.yaml    # Kubernetes Service manifest
└── README.md           # This file
```

## Usage

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/renancavalcantercb/kubernetes-ci-cd.git
   cd kubernetes-ci-cd
   ```

2. **Push Changes**:
   Push changes to the `main` branch to trigger the GitHub Actions workflow:

   ```bash
   git add .
   git commit -m "Trigger CI/CD pipeline"
   git push origin main
   ```

3. **Monitor Workflow**:
   Go to the repository's "Actions" tab to monitor the workflow execution.

## Notes

- The application image is tagged as `my-app:latest`. Modify the name in the workflow if necessary.
- Customize Kubernetes manifests in the `k8s/` directory to suit your application's requirements.
