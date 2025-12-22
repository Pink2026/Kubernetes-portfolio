# Kubernetes Application Deployment

This project demonstrates deploying a simple nginx application on Kubernetes.

## Features
- Deployment with 2 replicas
- Service of type NodePort
- Environment variables using ConfigMap
- Secret for sensitive data
- Liveness and readiness probes

## Demo
Screenshots in screenshots/ show the Deployment running, Service working, and nginx page response.

## How to run
1. Apply ConfigMap: kubectl apply -f configmap-config.yaml
2. Apply Secret: kubectl apply -f secret-config.yaml
3. Apply Deployment: kubectl apply -f deployment-config.yaml
4. Apply Service: kubectl apply -f service-config.yaml
5. Test with curl http://127.0.0.1:8080 in Killercoda
