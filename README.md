# GitOps-Based Kubernetes Deployment Using ArgoCD

## 🚀 Project Overview

This project sets up a GitOps-based Kubernetes deployment using ArgoCD, Terraform, and Helm. The goal is to automate the deployment process, enable rollback strategies, and set up a scalable infrastructure with monitoring and failover capabilities.

## ✅ Key Features

- Kubernetes cluster setup using Terraform on AWS (EKS).
- GitOps pipeline using ArgoCD for automated deployment.
- Helm for versioning and deployment management.
- Canary and Blue-Green deployment strategies.
- Monitoring with Prometheus and Grafana.
- Self-healing infrastructure with automatic recovery.

## 🏗️ Project Setup

### 1. Install Terraform and AWS CLI

```bash
# Install Terraform
brew install terraform    # For MacOS
sudo apt install terraform # For Ubuntu/Debian

# Install AWS CLI
brew install awscli
aws configure
```

> Add your AWS Access Key and Secret Key when prompted.

---

### 2. Create Terraform Configuration for EKS

Create a `main.tf` file:

### 3. Deploy with Terraform

```bash
terraform init
terraform validate
terraform apply -auto-approve
```

---

### 4. Configure `kubectl` for EKS

```bash
aws eks update-kubeconfig --name gitops-cluster --region us-west-2
kubectl get nodes
```

---

### 5. Install ArgoCD Using Helm

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm install argocd argo/argo-cd --namespace argocd --create-namespace
```

---

### 6. Access ArgoCD Dashboard

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

👉 Open [https://localhost:8080](https://localhost:8080)

Get the ArgoCD password:

```bash
kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

- **Username:** `admin`
- **Password:** Retrieved from the command above

---

### 7. Connect GitHub to ArgoCD

1. Create a GitHub repository for Kubernetes manifests.
2. Use ArgoCD to sync and deploy Kubernetes resources from the repository.

---

## 📊 Monitoring and Rollback

- Use Prometheus and Grafana for monitoring cluster health.
- Test rollback using `helm rollback`.

---

## 📅 Timeline

| Phase | Task | Estimated Time |
|-------|------|---------------|
| 1     | Kubernetes Cluster Setup | 1 Week |
| 2     | ArgoCD Installation + GitOps Setup | 1 Week |
| 3     | Canary + Blue-Green Deployment | 1 Week |
| 4     | Monitoring and Rollback Strategies | 1 Week |
| 5     | Testing + Documentation | 1 Week |

---

## 🌟 Why This Project Stands Out

✅ GitOps is a modern deployment strategy — valuable skill.  
✅ Shows expertise in Kubernetes, CI/CD, and Helm.  
✅ Demonstrates real-world deployment strategies and automation.
