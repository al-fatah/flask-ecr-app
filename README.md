# Flask App - CI/CD Pipeline to AWS ECR Using GitHub Actions

This project demonstrates a simple Flask application containerized with Docker and automatically pushed to a **private AWS Elastic Container Registry (ECR)** using **GitHub Actions CI/CD**.

The workflow builds and tags Docker images with:
- `latest`
- The GitHub commit SHA (`github.sha`) → ensuring **unique image versions**

---

## Project Structure
```
.
├── app.py
├── requirements.txt
├── Dockerfile
└── .github/
    └── workflows/
        └── ecr-push.yml
```

---

## Flask Application
A basic Flask application that exposes a simple web page at:
```
http://localhost:8080
```
Implemented in `app.py`.

---

## Dockerfile
The Dockerfile builds a Python environment, installs Flask, copies the application code, and exposes port **8080**.

---

## GitHub Actions Workflow
The CI/CD pipeline triggers automatically on:
```
push to main branch
```
The workflow will:
1. Configure AWS credentials
2. Log in to AWS ECR
3. Build Docker image
4. Tag it with `latest` and the commit SHA
5. Push both tags to the private ECR repository

Workflow file location:
```
.github/workflows/ecr-push.yml
```

---

## GitHub Secrets Required
Add these secrets in:
```
Settings → Secrets and variables → Actions
```

| Secret Name | Description |
|-------------|-------------|
| `AWS_ACCESS_KEY_ID` | IAM Access Key |
| `AWS_SECRET_ACCESS_KEY` | IAM Secret Key |

IAM user should have:
```
AmazonEC2ContainerRegistryFullAccess
```

---

## AWS ECR Repository
Create a private ECR repository named:
```
<your-name>-flask-private-repository
```
Example:
```
alfatah-flask-private-repository
```
Region: **ap-southeast-1 (Singapore)**

---

## Local Development (Optional)
Build image locally:
```bash
docker build -t flask-app .
docker run -p 8080:8080 flask-app
```
Visit:
```
http://localhost:8080
```

---

## Activity Requirements
### Activity 1
- Created public GitHub repository ✔️
- Added Flask app, Dockerfile, requirements.txt ✔️
- Created private AWS ECR repository ✔️
- Implemented GitHub Actions workflow using `github.sha` ✔️
- Automated build & push to ECR ✔️

---

## Submission
This repository contains all required deliverables including the Flask app, Dockerfile, and the GitHub Actions workflow used to build and push container images to AWS ECR.