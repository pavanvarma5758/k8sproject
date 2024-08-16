NGINX on Kubernetes: Deployment and Helm Chart
This repository provides resources for deploying an NGINX web server on a Kubernetes cluster. You can choose between deploying directly with Kubernetes manifests or using a Helm chart.

Supported options:

Kubernetes deployment
Helm chart deployment
Port forwarding for local access
Deployment customization via values.yaml
Requirements

A running Kubernetes cluster
kubectl installed and configured
Getting Started

Clone the repository:


git clone <repository-url>
cd <repository-directory>


Kubernetes Deployment
The deploy.yaml file defines the NGINX deployment.

Deploying NGINX:

Apply the deployment:


kubectl apply -f deploy.yaml


Verify the deployment:


kubectl get pods


This should show three pods running the NGINX image.

Helm Chart Deployment
This repository includes a Helm chart for deploying NGINX.

Deploying with Helm:

Install the chart:


helm install my-nginx .


Verify the deployment:


kubectl get pods


This should show three pods running NGINX managed by the Helm chart.

Accessing the NGINX Service
Port forward the service:


kubectl port-forward service/my-nginx 8080:80


Access the NGINX welcome page in your browser:

http://localhost:8080
You should see the default NGINX welcome page.

Customization (Helm Only)
Edit the values.yaml file to customize the deployment:

Replica Count: Number of NGINX pods (default: 1)
Image: Docker image details (repository, tag, pull policy)
Service: Service type (ClusterIP, NodePort, LoadBalancer) and port (default: 80)
Ingress: Enable Ingress for external access (default: disabled) with custom hostnames
Resources: Resource requests and limits for NGINX pods (CPU, memory)
Node Selector/Tolerations/Affinity: Configure pod scheduling behavior

Uninstalling NGINX (Helm only):
helm uninstall my-nginx

This removes all Kubernetes resources associated with the chart.

