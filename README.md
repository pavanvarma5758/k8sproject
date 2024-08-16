# nginx-chart

## Overview

This Helm chart deploys an NGINX web server on a Kubernetes cluster using a Kubernetes Deployment and Service. The chart is highly customizable, allowing you to configure various aspects such as replica count, image repository, service type, and more.

## Prerequisites

- Kubernetes 1.12+
- Helm 3.0+

## Installing the Chart

To install the chart with the release name `nginx-release`, run:


helm install nginx-release ./nginx-chart
This command installs the chart using default values from the values.yaml file.

Uninstalling the Chart
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
Accessing the NGINX Service
Using Port Forwarding
Run the following command to forward the port:



kubectl port-forward service/nginx-release-nginx-chart 8080:80
