# EKS Fargate + ALB Ingress (2048 Game)

This repo shows how I deployed the **2048 game** on **Amazon EKS using Fargate** and exposed it publicly using **AWS ALB Ingress** via the **AWS Load Balancer Controller**.

## Architecture

Browser → AWS ALB → Kubernetes Ingress → Service → Pods (Fargate)

## Why these choices

### Why EKS?
- Managed Kubernetes control plane (API server, etcd, scheduler)
- AWS-native networking and IAM integration

### Why Fargate?
- No EC2 worker nodes to manage
- AWS handles scaling/patching of compute
- Pay per pod resources

### Why Ingress (ALB) instead of NodePort/LoadBalancer?
- Production HTTP routing at Layer 7 (paths/hosts)
- One ALB can route multiple apps
- Easier TLS/HTTPS later using ACM

### Why AWS Load Balancer Controller?
- It watches Kubernetes Ingress and automatically creates ALB, target groups, and rules in AWS

### Why IRSA (IAM Roles for Service Accounts)?
- Secure AWS permissions without storing AWS keys in pods

---

## Step-by-step commands

### 1) Create EKS cluster with Fargate
```bash
eksctl create cluster --name demo-cluster --region us-east-1 --fargate
