# 🐳 Jenkins Docker-in-Docker CI/CD Pipeline

This project demonstrates a fully automated **CI/CD pipeline using Jenkins inside Docker**, designed to pull code from GitHub, build a Docker image, run containerized Spring Boot apps, and perform security and code quality analysis with **SonarQube** and **Trivy** — all within Docker!

---

## 🚀 What’s Inside

- 🔁 **Jenkins in Docker**: CI/CD orchestrated inside a Jenkins container  
- 🧪 **SonarQube Integration**: Static code analysis for code quality and bugs  
- 🛡️ **Trivy Scanner**: Container image vulnerability scanning  
- 🐳 **Docker-in-Docker (DinD)**: Jenkins builds and runs containers within its own container  
- 🔧 **Maven Build**: Compiles and packages a Spring Boot project  
- 🔁 **Automated Docker Image Build & Run**  
- 📦 **Docker Hub or Local Registry Push Support**

---

## 🔧 Requirements

Make sure the following are installed and running before setting up:

### 🖥️ Local Machine

- ✅ [Docker](https://docs.docker.com/get-docker/) (v20+ recommended)
- ✅ [Docker Compose](https://docs.docker.com/compose/)
- ✅ [Git](https://git-scm.com/)
- ✅ Internet connection to pull dependencies

### 🧪 Tools (via Docker or local installation)

- ✅ **Jenkins** (can run inside Docker)
- ✅ **SonarQube** (e.g., `http://localhost:9000`)
- ✅ **Trivy** (install locally or run via Docker)
- ✅ Java 17+ and Maven (for Spring Boot builds)

> 📝 All tools can be run using Docker containers for quick local setup.

---

## 📁 Folder Structure

```bash
.
├── Jenkinsfile               # Jenkins pipeline script
├── Dockerfile                # App Dockerfile (for Spring Boot app)
├── scripts/
│   └── docker-entrypoint.sh  # Optional custom script
├── src/                      # Spring Boot source code
├── pom.xml                   # Maven config
└── README.md                 # This file
