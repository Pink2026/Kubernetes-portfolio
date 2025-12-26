# CloudShop – Multi-Tier Kubernetes Application

## Project Overview
CloudShop is an e-commerce platform running a multi-tier application on Kubernetes.

This project demonstrates how a real production environment can be designed using Kubernetes best practices, including service isolation, health checks, autoscaling, and network security.

The application consists of:
- A *frontend web service* exposed to users
- A *backend service* accessible only from the frontend

---

## Architecture

Users
  |
Frontend Service (NodePort)
  |
Frontend Pods
  |
Backend Service (ClusterIP)
  |
Backend Pods

- The frontend is accessible externally
- The backend is internal and protected from direct access

---

## Kubernetes Concepts Demonstrated

- Namespaces for environment isolation
- Deployments for frontend and backend services
- Services
  - NodePort for frontend exposure
  - ClusterIP for backend internal access
- Liveness and Readiness probes
- Horizontal Pod Autoscaler (HPA)
- NetworkPolicy for pod-to-pod traffic control

---

## Key Features

### Health Checks
Both frontend and backend pods use liveness and readiness probes to ensure:
- Unhealthy containers are restarted automatically
- Traffic is routed only to healthy pods

### Autoscaling
The frontend deployment automatically scales based on CPU utilization using a Horizontal Pod Autoscaler to handle traffic spikes.

### Network Security
A NetworkPolicy restricts backend access so that:
- Only frontend pods can communicate with backend pods
- All other ingress traffic to backend pods is denied

This follows the principle of least privilege.

---

## How to Deploy

Apply the Kubernetes manifests in the following order:

kubectl apply -f namespace.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f backend-service.yaml
kubectl apply -f frontend-deployment.yaml
kubectl apply -f frontend-service.yaml
kubectl apply -f hpa.yaml
kubectl apply -f network-policy.yaml

---

## Validation

Verify the deployment using the following commands:

kubectl get pods -n cloudshop-prod
kubectl get svc -n cloudshop-prod
kubectl get hpa -n cloudshop-prod
kubectl get networkpolicy -n cloudshop-prod

Screenshots of the running resources and scaling behavior are available in the screenshots/ directory.

---

## Why This Project Matters

This project demonstrates the ability to:
- Design and deploy multi-tier Kubernetes applications
- Implement health checks and autoscaling
- Secure internal services using NetworkPolicies
- Apply production-ready Kubernetes architecture patterns

These skills are directly applicable to real-world Kubernetes and cloud-native environments.

---

## Skills Demonstrated
- Kubernetes architecture
- Application health management
- Autoscaling strategies
- Network security with NetworkPolicy
- Production-ready deployment practices
