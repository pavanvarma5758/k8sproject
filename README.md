# nginx-chart

## Overview

This Helm chart deploys an NGINX web server on a Kubernetes cluster using a Kubernetes Deployment and Service. The chart is highly customizable, allowing you to configure various aspects like replica count, image repository, service type, and more.

## Prerequisites

- Kubernetes 1.12+
- Helm 3.0+

## Installing the Chart

To install the chart with the release name `nginx-release`:

```
helm install nginx-release ./nginx-chart
This command installs the chart using default values from the values.yaml file.

Uninstalling the Chart
To uninstall the nginx-release:



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
Accessing the NGINX Service
Using Port Forwarding


kubectl port-forward service/nginx-release-nginx-chart 8080:80
Access the NGINX service at http://localhost:8080.

Using NodePort
If you have changed the service type to NodePort, you can access the service via the node's IP and assigned port.



minikube service nginx-release-nginx-chart --url
Using Ingress
If Ingress is enabled and configured, access the service using the specified host:



http://<your-ingress-host>
Values
Below is a list of all configurable values from the values.yaml file and their default settings:

yaml

replicaCount: 1

image:
  repository: nginx
  pullPolicy: IfNotPresent
  tag: ""

service:
  type: ClusterIP
  port: 80

ingress:
  enabled: false
  className: ""
  annotations: {}
  hosts:
    - host: chart-example.local
      paths:
        - path: /
          pathType: ImplementationSpecific
  tls: []

resources: {}

nodeSelector: {}

tolerations: []

affinity: {}
