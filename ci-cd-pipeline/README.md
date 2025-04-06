---
### **ci-cd-pipeline/README.md**

# CI/CD Pipeline Project (Jenkins + Ansible)

This project demonstrates a complete CI/CD pipeline using Jenkins for automation and Ansible for deployment. The pipeline includes source code checkout, build, unit testing, Docker image creation, security scanning, and deployment to AWS/GCP.

---

## 🧱 Architecture Overview

```
        ┌────────────┐
        │ Developer  │
        └─────┬──────┘
              │ Git Push
        ┌─────▼────────────┐
        │ GitHub Repository│
        └─────┬────────────┘
              │ Webhook
        ┌─────▼────────────┐
        │ Jenkins Server   │
        └─────┬────────────┘
              │ Jenkinsfile pipeline
        ┌─────▼────────────┐
        │ Build & Test     │
        └─────┬────────────┘
              │ Docker Build/Push
        ┌─────▼────────────┐
        │ Docker Registry  │
        └─────┬────────────┘
              │ Ansible Deploy
        ┌─────▼────────────┐
        │ AWS/GCP Servers  │
        └──────────────────┘
```

---

## 📁 Folder Structure

```
ci-cd-pipeline/
├── ansible/
│   ├── inventory.ini
│   └── playbook.yml
├── Jenkinsfile
├── build.sh
├── test/
│   └── unit_test.sh
├── deploy/
│   └── deploy.sh
├── docker/
│   └── Dockerfile
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- Jenkins installed with required plugins
- Ansible installed on Jenkins or separate deploy node
- Docker & Git installed
- AWS or GCP instance(s) for deployment

### Jenkinsfile Sample
```groovy
pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/your-org/sample-app.git'
      }
    }
    stage('Build') {
      steps {
        sh './build.sh'
      }
    }
    stage('Test') {
      steps {
        sh './test/unit_test.sh'
      }
    }
    stage('Docker Build & Push') {
      steps {
        sh 'docker build -t my-app:latest .'
        sh 'docker tag my-app:latest <registry>/my-app:latest'
        sh 'docker push <registry>/my-app:latest'
      }
    }
    stage('Deploy') {
      steps {
        sh 'ansible-playbook -i ansible/inventory.ini ansible/playbook.yml'
      }
    }
  }
}
```

---

## 🔐 Security & Best Practices
- Use credentials binding for registry login
- Secrets stored in Jenkins Credentials Manager
- Linting and static analysis (e.g., hadolint)
- Slack/email notifications



