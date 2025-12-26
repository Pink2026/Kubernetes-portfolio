# CloudShop – Production-Grade Kubernetes Platform

## Project Overview
CloudShop is a simulated production e-commerce platform deployed on Kubernetes following real-world architectural and security best practices.

This project focuses on *secure traffic management*, *application reliability*, and *zero-trust networking*, similar to what is used in enterprise Kubernetes environments.

---

## Architecture Overview

Internet Users
      |
   Ingress
      |
Frontend Service (ClusterIP)
      |
Frontend Pods
      |
Backend Service (ClusterIP)
      |
Backend Pods

### Key Design Decisions
- External traffic enters the cluster *only through Ingress*
- Internal services are *never exposed directly*
- Backend access is restricted using *NetworkPolicies*
- Applications are protected with *health probes*

---

## Kubernetes Concepts Demonstrated

- Namespaces for environment isolation
- Deployments with replicas for high availability
- Services (ClusterIP) for internal communication
- Ingress for controlled external access
- Liveness & Readiness probes for self-healing
- NetworkPolicy for zero-trust security
- Labels and selectors for clean service routing

---

## Security Model

### Zero-Trust Networking
- Backend pods *only accept traffic from frontend pods*
- All other ingress traffic to backend pods is denied by default
- This follows the principle of least privilege

### Controlled Exposure
- Only the frontend is reachable via Ingress
- No NodePort or LoadBalancer services are used

---

## Reliability & Health

- *Liveness probes* ensure unhealthy containers are restarted
- *Readiness probes* prevent traffic from reaching unready pods
- Multiple replicas ensure service availability during failures

---

## Deployment Instructions

Apply the manifests in the following order:

kubectl apply -f namespace.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f backend-service.yaml
kubectl apply -f frontend-deployment.yaml
kubectl apply -f frontend-service.yaml
kubectl apply -f ingress.yaml
kubectl apply -f network-policy.yaml

---

## Validation

Verify that all components are running correctly:

kubectl get pods -n cloudshop-platform
kubectl get svc -n cloudshop-platform
kubectl get ingress -n cloudshop-platform
kubectl get networkpolicy -n cloudshop-platform

Screenshots of the running environment and resources are available in the screenshots/ directory.

---

## Why This Project Matters

This project demonstrates the ability to:
- Design production-ready Kubernetes architectures
- Secure internal services using network isolation
- Manage external traffic using Ingress
- Build reliable and self-healing applications
- Apply real-world Kubernetes security patterns

These skills are directly applicable to *DevOps*, *Platform Engineering*, and *Cloud Engineering* roles.

---

## Skills Demonstrated
- Kubernetes production architecture
- Secure service exposure
- Network security with NetworkPolicy
- Application health management
- Real-world Kubernetes deployment practices
