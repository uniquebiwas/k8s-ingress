# Kubernetes Ingress Deployment for Applications
### This repository contains Kubernetes manifests to deploy and expose multiple applications (app1, app2, app3, and app4) using an Ingress controller. The setup supports both physical server environments and cloud platforms (AWS, GCP, Azure).

Features
Deployment files for applications: app1, app2, app3, and app4.
Ingress configuration to route traffic to these applications.
Compatibility with physical servers and major cloud providers.
Step-by-step instructions to set up and validate the deployment.
Example screenshots included for verification.
Prerequisites
Kubernetes Cluster

Ensure you have a Kubernetes cluster running (on-premises or in the cloud).
Ingress Controller

A functional ingress controller is required. If you are using:
Physical Servers: Use NGINX Ingress Controller installed via Helm.
Cloud Platforms: Use the native ingress controller provided by your cloud provider.
Tools

kubectl installed and configured to access your cluster.
Helm installed for managing the NGINX ingress controller.
Setup Instructions
1. Install the Ingress Controller
a. For Physical Servers or Generic Kubernetes Clusters
Install the NGINX Ingress Controller using Helm:


# Add the NGINX Ingress repository

```bash 
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
```
# Update Helm repositories

```bash 
helm repo update
```
# Install the NGINX Ingress Controller

```bash 
helm install nginx-ingress ingress-nginx/ingress-nginx --set controller.publishService.enabled=true 
```

b. For Cloud Platforms
Use the cloud provider's native ingress controller:

AWS: AWS ALB Ingress Controller
GCP: GCP Load Balancer Ingress
Azure: Azure Application Gateway Ingress Controller

2. Deploy the Applications
Deploy the application manifests in your cluster. Run the following commands:

```bash
kubectl apply -f app1-deployment.yaml
kubectl apply -f app2-deployment.yaml
kubectl apply -f app3-deployment.yaml
kubectl apply -f app4-deployment.yaml
```
3. Apply the Ingress Configuration
Deploy the ingress manifest to configure traffic routing:

```bash
kubectl apply -f ingress.yaml
```
Ingress routes traffic as follows:

app1.biwaspudasaini.com.np → Service for app1.service
app2.biwaspudasaini.com.np → Service for app2.service
app3.biwaspudasaini.com.np → Service for app3.service
app4.biwaspudasaini.com.np → Service for app4.service

4. Verify the Deployment
Check the ingress setup:

```bash
kubectl get ingress
```
Note the external IP or DNS name provided.

Access the applications:

Confirm functionality using the example screenshots in the screenshots directory.

Screenshots
The screenshots is in this repository contains:

Ingress resource details
Application outputs accessed via ingress routes
These examples will help you validate the correctness of the deployment.


If using HTTPS, modify the ingress.yaml file to include TLS certificates.
Cloud provider ingress controllers may have additional configuration steps.