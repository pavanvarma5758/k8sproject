### NGINX on Kubernetes: Deployment and Helm Chart

This repository provides resources for deploying an NGINX web server on a Kubernetes cluster. You can choose between deploying directly with Kubernetes manifests or using a Helm chart.

A running Kubernetes cluster
kubectl installed and configured
Getting Started

Clone the repository:

git clone https://github.com/pavanvarma5758/k8sproject

cd k8sproject


> Kubernetes Deployment

The deploy.yaml file defines the NGINX deployment.

Apply the deployment with this command 

kubectl apply -f deploy.yaml

Verify the deployment with the command 

kubectl get pods


This should show three pods running the NGINX image.
![Screen Shot 2024-08-16 at 2 37 23 PM](https://github.com/user-attachments/assets/4628ad57-e472-4a04-a156-69fd7f4270b9)


Helm Chart Deployment
This repository includes a Helm chart for deploying NGINX.

Deploying with Helm:

Install the chart:


helm install my-nginx .


we can Verify the deployment with this command

kubectl get pods

we will get output like this 

![Screen Shot 2024-08-16 at 2 43 40 PM](https://github.com/user-attachments/assets/0fed7935-0922-4e59-93aa-1502608695bf)



This should show three pods running NGINX managed by the Helm chart.

Accessing the NGINX Service
Port forward the service:


kubectl port-forward service/my-nginx 8080:80


Access the NGINX welcome page in your browser:

http://localhost:8080
You should see the default NGINX welcome page.

![Screen Shot 2024-08-16 at 2 46 25 PM](https://github.com/user-attachments/assets/30e66149-f866-43d4-ba83-309a6cf9b7d3)


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

