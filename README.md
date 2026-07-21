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
├── Service NodePort
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
```

### 2️⃣ Apply Namespace

```bash
kubectl apply -f namespace.yml
```

### 3️⃣ Create Storage

```bash
kubectl apply -f pv.yml
kubectl apply -f pvc.yml
```

### 4️⃣ Deploy Application

```bash
kubectl apply -f deployment.yml
```

### 5️⃣ Expose Service

```bash
kubectl apply -f service.yml
```
## ✅ Verify Deployment

```bash
kubectl get all -n quantumapp
kubectl get pv
kubectl get pvc -n quantumapp
kubectl get svc -n quantumapp
```

Expected output:

```text
NAME               TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)
quantum-service    NodePort   10.x.x.x        <none>        8000:30080/TCP
```

🌐 Access Application
Open in browser:

http://<EC2-Public-IP>:30080

🌐 Access Application
Using port-forward:

kubectl port-forward --address 0.0.0.0 svc/quantum-service 8000:8000 -n quantumapp

QUANTUM-APP
<img width="957" height="534" alt="image" src="https://github.com/user-attachments/assets/15579b26-c78d-4452-9bae-08f843bcc2d1" />

RESULTS
<img width="1039" height="645" alt="image" src="https://github.com/user-attachments/assets/bc890590-a498-4371-ad99-d5c1ca85e902" />

PREDICTION ACTIVE
<img width="904" height="589" alt="image" src="https://github.com/user-attachments/assets/99b801e1-7c33-43f6-93af-0514ec992192" />

PREDICTION INACTIVE
<img width="935" height="615" alt="image" src="https://github.com/user-attachments/assets/f05011d2-ca68-4b9a-9309-19a50ae952fa" />

PREDICTION INVALID
<img width="857" height="550" alt="image" src="https://github.com/user-attachments/assets/4520c66e-f749-4ed8-b439-9c8920e5f4bc" />

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
