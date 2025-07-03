# Docker Voting App with Azure DevOps CI/CD

A modernized version of the classic Docker Voting App example with enterprise-grade CI/CD using Azure DevOps and GitOps practices.

## 🚀 Project Overview

This project transforms the original [Docker Voting App](https://github.com/dockersamples/example-voting-app) into a production-ready application with modern DevOps practices.

## 🏗️ What I Built

**Original Setup:**
- Simple Docker Compose application
- Basic GitHub Actions CI/CD

**My Implementation:**
- **3 separate Azure DevOps pipelines** for each microservice
- **Path-based triggers** instead of branch triggers
- **Self-hosted Azure VM runner** for builds
- **Azure Container Registry** for image storage
- **ArgoCD GitOps** for automated deployments

## 🔧 Architecture

The application has three microservices:
1. **Voting Service** - Frontend for casting votes
2. **Result Service** - Display voting results
3. **Worker Service** - Background vote processing

Each service has its own dedicated pipeline that only triggers when files in that service's directory change.

## 📋 Pipeline Structure

Each of the 3 pipelines follows the same pattern:

1. **Build Stage** - Compile and test the application
2. **Push Stage** - Build Docker image and push to Azure Container Registry
3. **Update Stage** - Update Kubernetes manifests with new image tags

## 🔄 How It Works

1. **Code Change** → Developer modifies code in `/vote/`, `/result/`, or `/worker/` directory
2. **Pipeline Trigger** → Only the relevant service pipeline runs (not all 3)
3. **Automated Build** → Code is built, tested, and containerized
4. **Image Push** → Docker image pushed to Azure Container Registry
5. **GitOps Update** → ArgoCD automatically deploys the new version

## 🛠️ Key Technologies

- **Azure DevOps** - CI/CD pipelines
- **Azure Container Registry** - Image storage
- **Azure VM** - Self-hosted build agent
- **ArgoCD** - GitOps deployment
- **Kubernetes** - Container orchestration
- **Docker** - Containerization

## 📈 Improvements Made

| Feature | Original | My Version |
|---------|----------|------------|
| CI/CD | GitHub Actions | Azure DevOps |
| Registry | Docker Hub | Azure Container Registry |
| Build Agent | GitHub-hosted | Self-hosted Azure VM |

## 🎯 Why This Approach?

- **Efficiency**: Only build and deploy what changed
- **Scalability**: Each service can be developed independently
- **Security**: Private container registry and controlled build environment
- **Reliability**: GitOps ensures consistent deployments
- **Enterprise-Ready**: Follows industry best practices

