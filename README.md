# EKS Fargate + ALB Ingress (2048 Game)

This repository demonstrates deploying the **2048 game** on **Amazon EKS** using **AWS Fargate** and exposing it publicly using an **Application Load Balancer (ALB)** through **Kubernetes Ingress**.

---

## What I Did

- Created an **Amazon EKS cluster** with **Fargate** to run Kubernetes workloads without managing EC2 nodes
- Created a **namespace (`game-2048`)** to isolate the application
- Configured a **Fargate profile** so pods in the namespace run on Fargate
- Deployed the **2048 game** using Kubernetes **Deployment**, **Service**, and **Ingress**
- Installed the **AWS Load Balancer Controller** to manage ALB resources
- Used **IRSA (IAM Roles for Service Accounts)** for secure AWS permissions
- Exposed the application publicly using an **AWS Application Load Balancer**

---

## Architecture

Browser → AWS ALB → Kubernetes Ingress → Service → Pods (Fargate)


---

## Kubernetes Resources Used

- Namespace
- Deployment
- Service (NodePort)
- Ingress (ALB)
- Fargate Profile
- IAM Service Account (IRSA)

---

## Application

- **App:** 2048 Game
- **Source YAML:**  
  https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/examples/2048/2048_full.yaml
- **Access:** Via ALB DNS name created by Ingress

---

## Outcome

- Application runs fully on **serverless Kubernetes (Fargate)**
- Traffic is routed using **ALB Ingress**
- No EC2 worker nodes required
- Follows AWS production best practices

---

## Screenshot

<img width="1440" alt="2048 Game Running on EKS" src="https://github.com/user-attachments/assets/536b6e5a-1feb-4e8e-b000-d9c23e767267" />

---

## Author

**Saketh Reddy**  
Cloud / DevOps Engineer


