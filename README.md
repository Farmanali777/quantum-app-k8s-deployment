# 🚀 Quantum Drug Discovery App - Kubernetes Deployment

This repository contains Kubernetes manifests to deploy a **Quantum Drug Discovery Application** built using Flask, Docker, and a Kind multi-node cluster.

---

## 📌 Project Overview

This project demonstrates a complete **DevOps workflow**:

- Containerization using Docker
- Multi-node Kubernetes cluster using Kind
- Deployment with scalability (replicas)
- Persistent storage using PV & PVC
- Service exposure for application access

---

## 🏗️ Architecture


Namespace (quantumapp)
│
├── Deployment (2 replicas)
│ └── Pods (running app)
│
├── Service ClusterIP
│
├── Persistent Volume (PV)
│
└── Persistent Volume Claim (PVC)


---

## ⚙️ Technologies Used

- Kubernetes (Kind cluster)
- Docker
- Flask (Python)
- Quantum ML (Qiskit, PennyLane, RDKit)
- YAML (K8s manifests)

---

## 📂 Kubernetes Manifests

| File | Description |
|------|------------|
| `namespace.yml` | Creates namespace |
| `deployment.yml` | Deploys application pods |
| `service.yml` | Exposes the application |
| `pv.yml` | Persistent Volume |
| `pvc.yml` | Persistent Volume Claim |
| `configmap.yml` | Configuration (optional) |
| `kind-config.yml` | Kind cluster configuration |

---

## 🚀 Deployment Steps

### 1️⃣ Create Kind Cluster

```bash
kind create cluster --config kind-config.yml

2️⃣ Apply Namespace
kubectl apply -f namespace.yml

3️⃣ Create Storage
kubectl apply -f pv.yml
kubectl apply -f pvc.yml

4️⃣ Deploy Application
kubectl apply -f deployment.yml

5️⃣ Expose Service
kubectl apply -f service.yml

🌐 Access Application
Using port-forward:

kubectl port-forward --address 0.0.0.0 svc/quantum-service 8000:8000 -n quantumapp

Open in browser:

http://<EC2-IP>:8000

📊 Features
Multi-node Kubernetes deployment
Load balancing across pods
Persistent storage support
Scalable architecture
Clean DevOps structure

👨‍💻 Author
Farman Ali

DevOps | Cloud | Kubernetes
Focused on building real-world production-level projects
