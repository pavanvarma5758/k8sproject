# NGINX Kubernetes Deployment and Helm Chart

This repository contains the resources needed to deploy an NGINX web server on a Kubernetes cluster. The deployment can be done using raw Kubernetes manifests or through Helm charts.

## Kubernetes Deployment

You can deploy the NGINX web server directly using the provided `deploy.yaml` file.

### Steps:

1. Clone the repository:
   ```
   git clone <repository-url>
   cd <repository-directory>

Apply the Kubernetes deployment:

kubectl apply -f deploy.yaml

you can verify it by giving the below command 

kubectl get pods 

you will get output like this 

NAME                                        READY   STATUS    RESTARTS      AGE
nginx-deployment-6b7f675859-2c2s7           1/1     Running   1 (48m ago)   4h28m
nginx-deployment-6b7f675859-6ppn5           1/1     Running   1 (48m ago)   4h28m
nginx-deployment-6b7f675859-954jd           1/1     Running   1 (48m ago)   4h28m


Helm Chart Deployment
Alternatively, you can deploy using the Helm chart included in this repository.

Steps:

Install the Helm chart:

helm install my-nginx .

you can verify pods by giving the below command 

kubectl get pods

you will get output like this 

NAME                                        READY   STATUS    RESTARTS      AGE
nginx-release-nginx-chart-dbf8b8f5b-2z629   1/1     Running   1 (48m ago)   4h11m
nginx-release-nginx-chart-dbf8b8f5b-g2g4d   1/1     Running   1 (48m ago)   4h11m
nginx-release-nginx-chart-dbf8b8f5b-kn5dj   1/1     Running   1 (48m ago)   4h11m


Accessing the NGINX Service Using Port Forwarding
Run the following command to forward the port:

kubectl port-forward service/nginx-release-nginx-chart 8080:80

now we can access the local host with 8080 port #localhost:8080

you can see the default nginx webpage like this 

Welcome to nginx!
If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.
Thank you for using nginx.

Customizing the Deployment
You can customize the deployment by editing the values.yaml file before running the helm install command


To uninstall the nginx-release, run:



helm uninstall nginx-release
This command removes all Kubernetes components associated with the chart.

Configuration
The values.yaml file allows you to customize the deployment. Below are some of the key configurable parameters:

Replica Count
Parameter: replicaCount
Description: Number of replicas for the NGINX Deployment.
Default: 1
Image
Parameter: image.repository

Description: NGINX Docker image repository.

Default: nginx

Parameter: image.tag

Description: NGINX Docker image tag.

Default: "" (uses the app version)

Parameter: image.pullPolicy

Description: Image pull policy.

Default: IfNotPresent

Service
Parameter: service.type

Description: Kubernetes service type. Options: ClusterIP, NodePort, LoadBalancer.

Default: ClusterIP

Parameter: service.port

Description: Service port.

Default: 80

Ingress
Parameter: ingress.enabled

Description: Enable Ingress for the service.

Default: false

Parameter: ingress.hosts

Description: List of Ingress hosts.

Default: chart-example.local

Resources
Parameter: resources
Description: CPU and memory resource requests and limits.
Default: {}
NodeSelector, Tolerations, and Affinity
Parameters: nodeSelector, tolerations, affinity
Description: Configurations for pod scheduling.
Default: {}









