# MarketingCloud – Kubernetes RBAC & Security

## Project Context
MarketingCloud is an e-commerce platform running applications on Kubernetes.

The marketing team needs to *monitor the frontend applications* by checking pod status, but they *must not be able to create, delete, or modify resources*.

This project demonstrates how Kubernetes *Role-Based Access Control (RBAC)* can be used to give *read-only access* in a safe and controlled way.

---

## What This Project Shows
- Namespace isolation for frontend applications
- A ServiceAccount representing a non-technical team (marketing)
- A Role that allows *read-only access to pods*
- A RoleBinding that connects the ServiceAccount to the Role
- Permission testing using kubectl impersonation

---

## Kubernetes Resources Used
- Namespace
- ServiceAccount
- Role
- RoleBinding

---

## How to Deploy
Apply the resources in the following order:
kubectl apply -f namespace.yaml
kubectl apply -f serviceaccount.yaml
kubectl apply -f role.yaml
kubectl apply -f rolebinding.yaml

---


## How Permissions Were Tested
Access was verified using Kubernetes impersonation:

kubectl auth can-i create pods \--as=system:serviceaccount:marketing-frontend:marketing-viewer \ -n marketing-frontend

kubectl auth can-i get pods \--as=system:serviceaccount:marketing-frontend:marketing-viewer \-n marketing-frontend
