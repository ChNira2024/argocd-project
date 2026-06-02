# argocd-project
# 🚀 ArgoCD GitOps Deployment – Microservices Project

## 📌 Project Overview
## Please follow above present .txt file inside my-project folder to get the execution steps 

This project demonstrates **GitOps-based deployment using ArgoCD** on a Kubernetes cluster (Kind).
It includes a **microservices-based tax-price calculation system** with frontend and backend services.

---

## 🧰 Tech Stack

* ☕ Spring Boot (Backend Services)
* ⚛️ React (Frontend)
* 🐳 Docker (Containerization)
* ☸️ Kubernetes (Kind Cluster - Local Setup)
* 🔄 ArgoCD (GitOps Continuous Deployment)
* 🐙 GitHub (Source of Truth)

---

## 🏗️ Architecture

Frontend (React) → Price Service → Tax Service

* Frontend calls Price API
* Price service internally calls Tax service
* ArgoCD syncs all Kubernetes manifests from GitHub

---

## 📂 Repository Structure

```
microservices-tax-price-calculation/
├── tax-service/
│   ├── deployment.yaml
│   └── service.yaml
├── price-service/
│   ├── deployment.yaml
│   └── service.yaml
├── tax-price-calculation-react/
│   ├── deployment.yaml
│   └── service.yaml
```

---

## ⚙️ Setup Instructions

### 1️⃣ Start Kubernetes Cluster (Kind)

```bash
kind create cluster --name argocd-cluster
```

---

### 2️⃣ Install ArgoCD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

---

### 3️⃣ Access ArgoCD UI

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Open:

```
https://localhost:8080
```

---

### 4️⃣ Login Credentials

```bash
kubectl get secret argocd-initial-admin-secret -n argocd \
-o jsonpath="{.data.password}" | base64 -d
```

* Username: `admin`
* Password: (above command output)
### Please follow .txt file above added , there u can get all the steps and how to customize your own password

---

### 5️⃣ Create ArgoCD Applications

Create separate applications for each service:

* tax-service
* price-service
* frontend (React)

---

## 🔄 GitOps Workflow

1. Push Kubernetes YAML changes to GitHub
2. ArgoCD detects changes automatically
3. Syncs changes to Kubernetes cluster
4. Application state remains consistent

---

## 📸 ArgoCD Dashboard

* Applications show **Healthy + Synced**
* Easy monitoring of deployments
* Real-time sync status

---

## 💡 Key Learnings

* Understanding GitOps principles
* Managing multi-service deployments
* Handling Kubernetes networking & services
* Automating deployments using ArgoCD

---

## 🚀 Future Improvements

* Add Ingress for single URL access
* Implement CI pipeline (GitHub Actions)
* Add monitoring (Prometheus + Grafana)

---

## 🔗 GitHub Repository

👉 https://github.com/ChNira2024/docker-k8s-deployment

---

## 🙌 Conclusion

This project helped me gain hands-on experience with **modern DevOps practices**, especially GitOps using ArgoCD.

---

## 📢 Connect with Me

Feel free to connect on LinkedIn for collaboration and discussions on DevOps & Microservices 🚀
