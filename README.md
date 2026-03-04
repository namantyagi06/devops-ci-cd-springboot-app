<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/38eec8df-12b0-4c09-be0a-d8d7a7793df6" />

# 🚀 End-to-End DevOps CI/CD Pipeline with Jenkins, SonarQube, Docker, ArgoCD & Kubernetes

This project demonstrates a **complete GitOps-based CI/CD pipeline** for a Spring Boot application using modern DevOps tools. The pipeline automatically builds, tests, analyzes, containerizes, and deploys the application to a Kubernetes cluster.

---

# 📌 Project Architecture

The CI/CD pipeline follows this workflow:

Developer → GitHub → Jenkins → Maven Build → SonarQube Analysis → Docker Build → DockerHub → Update Kubernetes Manifest → ArgoCD → Kubernetes Deployment

---

# 🛠️ Tools & Technologies Used

| Tool       | Purpose                                  |
| ---------- | ---------------------------------------- |
| GitHub     | Source code repository                   |
| Jenkins    | CI/CD pipeline automation                |
| Maven      | Build automation & dependency management |
| SonarQube  | Static code analysis & quality checks    |
| Docker     | Containerization                         |
| DockerHub  | Container image registry                 |
| ArgoCD     | GitOps continuous deployment             |
| Kubernetes | Container orchestration platform         |

---

# ⚙️ CI/CD Pipeline Flow

## 1️⃣ Code Commit

Developers push the application code to the GitHub repository.

```
git push origin main
```

---

## 2️⃣ Jenkins Pipeline Trigger

Jenkins automatically triggers the pipeline and reads the **Jenkinsfile** from the repository.

---

## 3️⃣ Build & Test (Maven)

Maven builds the Spring Boot application and generates the executable JAR.

Steps performed:

* Compile the source code
* Run unit tests
* Package the application

Command executed:

```
mvn clean package
```

Output:

```
target/spring-boot-demo.jar
```

---

## 4️⃣ Static Code Analysis (SonarQube)

SonarQube performs static code analysis to detect:

* Bugs
* Vulnerabilities
* Code smells
* Code coverage

Command executed:

```
mvn sonar:sonar
```

---

## 5️⃣ Docker Image Build

The application is containerized using Docker.

```
docker build -t <dockerhub-username>/ultimate-cicd:${BUILD_NUMBER} .
```

Example image:

```
namantyagi06/ultimate-cicd:15
```

---

## 6️⃣ Push Image to DockerHub

The built Docker image is pushed to DockerHub.

```
docker push namantyagi06/ultimate-cicd:${BUILD_NUMBER}
```

---

## 7️⃣ Update Kubernetes Deployment Manifest

Jenkins automatically updates the Kubernetes deployment YAML file with the new image tag.

Example:

```
image: namantyagi06/ultimate-cicd:15
```

The updated manifest is then committed and pushed back to GitHub.

---

## 8️⃣ GitOps Deployment with ArgoCD

ArgoCD continuously monitors the Git repository for changes.

Once a change is detected:

* ArgoCD syncs the manifests
* The application is automatically deployed to Kubernetes

---

## 9️⃣ Application Deployment on Kubernetes

Kubernetes creates and manages:

* Deployments
* Pods
* Services

The application becomes accessible after successful deployment.

---

# 📊 CI/CD Pipeline Diagram

Refer to the architecture diagram below:

![CI/CD Pipeline](cicd-architecture.png)

---

# 📂 Project Structure

```
Jenkins-Zero-To-Hero
│
├── java-maven-sonar-argocd-helm-k8s
│
├── spring-boot-app
│   ├── src
│   ├── Dockerfile
│   ├── Jenkinsfile
│   └── pom.xml
│
├── spring-boot-app-manifests
│   └── deployment.yml
```

---

# 🚀 Key Features

✔ Automated CI/CD pipeline
✔ Static code quality analysis
✔ Docker containerization
✔ GitOps deployment using ArgoCD
✔ Kubernetes automated deployment

---

# 📌 Future Improvements

* Add **Trivy container security scanning**
* Implement **SonarQube Quality Gate**
* Add **Helm for Kubernetes package management**
* Implement **Monitoring using Prometheus & Grafana**

---

# 👨‍💻 Author

**Naman Tyagi**

DevOps & Cloud Enthusiast

GitHub:
https://github.com/namantyagi06
