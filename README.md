# 🛒 Ekart - CI/CD Pipeline Project

A production-ready Java-based ecommerce backend application, integrated with a complete CI/CD pipeline using Jenkins, SonarQube, Trivy, Docker, and Email Notifications.

## 📦 Tech Stack

- Java 17
- Maven
- Spring Boot
- Docker
- Jenkins (Pipeline as Code)
- SonarQube (Code Quality)
- Trivy (Security Scanning)
- HTML Email Notification (Post-build report)

## 🚀 Pipeline Overview

This Jenkinsfile automates the complete DevOps lifecycle:

| Stage                | Description                                                    |
|---------------------|----------------------------------------------------------------|
| Git Checkout        | Clones the Ekart GitHub repo                                   |
| Compile             | Compiles the source code using Maven                           |
| SonarQube Analysis  | Performs static code analysis with SonarQube                   |
| Test                | Runs unit tests (optional: currently skipped)                  |
| File System Scan    | Security scan on source code using Trivy                       |
| Build               | Builds the JAR using Maven                                     |
| Docker Build        | Builds Docker image using `docker/Dockerfile`                 |
| Image Scan          | Trivy image scan for vulnerabilities                           |
| Docker Run          | Deploys Docker container on port `8070`                        |
| Email Notification  | Sends styled HTML email with pipeline summary + Trivy report  |

## ✅ Prerequisites

Ensure these tools are installed and configured:

- Docker
- Java 17
- Maven 3.x
- Jenkins with:
  - `jdk17`, `maven3`, `sonar-scanner` configured via global tools
  - SonarQube plugin + credentials configured (`sonar`)
  - Email Notification (SMTP setup)
  - Trivy installed on Jenkins machine

## 🔧 Setup Commands

Use the following shell commands to run/debug manually:

```bash
# Clone repo
git clone https://github.com/jaiswaladi246/Ekart.git
cd Ekart

# Compile code
mvn clean compile

# SonarQube scan
sonar-scanner -Dsonar.projectKey=Ekart \
              -Dsonar.projectName=Ekart \
              -Dsonar.java.binaries=. \
              -Dsonar.host.url=http://<sonar-host>:9000 \
              -Dsonar.login=<your_token>

# Trivy scan (File System)
trivy fs --format table -o trivy-fs-report.html .

# Build project
mvn clean install -DskipTests

# Build Docker image
docker build -f docker/Dockerfile -t ekart-app:latest .

# Trivy scan (Docker image)
trivy image --format table -o trivy-image-report.html ekart-app:latest

# Run container
docker rm -f ekart || true
docker run -d --name ekart -p 8070:8070 ekart-app:latest
