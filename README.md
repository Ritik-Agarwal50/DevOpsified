# README.md

## Overview

This project is containerized using Docker and deployed on AWS EKS using Kubernetes. The setup includes a multi-stage Dockerfile for efficient image building and Kubernetes manifests for deployment, services, and ingress.

## Prerequisites

Before you begin, ensure you have the following tools installed:

- **Docker:** For containerization.
- **kubectl:** CLI for working with Kubernetes clusters.
- **AWS CLI:** CLI for interacting with AWS services. Configure it using your AWS access key.
- **eksctl:** CLI for working with EKS clusters.

## Steps

### 1. Containerization

1. **Understand the Project Flow**
   - Determine how the project works.
   - Identify the port the project runs on.

2. **Build a Multi-Stage Dockerfile**
   - Multi-stage builds help optimize the image size and improve build performance.

### 2. Kubernetes Manifests

1. **Create `deployment.yml` Script**
   - Define the deployment configuration for the project.

2. **Create `services.yml` Script**
   - Define the service configuration for the project.

3. **Create `ingress.yml` Script**
   - Define the ingress configuration for the project.

### 3. Deploy the Project on AWS EKS

To deploy the project on AWS EKS, follow these steps:

1. **Install Prerequisites**
   - Ensure `kubectl`, `AWS CLI`, and `eksctl` are installed and configured.

2. **Create an EKS Cluster**
   - Use the following command to create an EKS cluster:
     ```sh
     eksctl create cluster --name demo-cluster --region <enter your region like ap-south-1>
     ```

3. **Apply Kubernetes Manifests**
   - Use `kubectl apply -f` command to deploy the `deployment.yml`, `services.yml`, and `ingress.yml` files.

4. **Delete the EKS Cluster**
   - Use the following command to delete the EKS cluster:
     ```sh
     eksctl delete cluster --name demo-cluster --region <enter your region which you used above>
     ```
5. **Nginx Ingress controler Config**
    Ingress controller is bascially a Go lang program which will look at you ingress reosurces and  it will create load balance as per the ingress resources.

   - Use this to deply Nginx Ingress controller
      ```sh
      kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.1/deploy/static/provider/aws/deploy.yaml
      ```
6. **Grab the Address of ingress and bind it to the respective IP address**
   - Use this to fetch the Ingress Address:
      ```sh
      kubectl get ing
      ```
   - Use this to get IP address:
     ```sh
      nslookup <put the ingress address>
      ```
   - Use this to do DNS mapping:
     ```sh
     sudo vim /etc/host
     ```
   - Bind the IP with the a host name like <go-web-app.local>
   - After completing these all process you access your app on your specific hostname.

7. **Now create Helm chart creation**
   - 
