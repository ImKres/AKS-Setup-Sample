# AKS Setup Sample
This project demonstrates how to deploy a simple Node.js application to Azure Kubernetes Service (AKS).

## Prerequisites

- Azure CLI
- Kubectl
- Docker

## Getting Started

### 1. Clone the Repository

- git clone https://github.com/your_username/aks-setup-sample.git
- cd aks-setup-sample

### 2. Build and Push Docker Image

Login to Docker Hub
- docker login

Build the Docker image
- docker build -t your_dockerhub_username/aks-setup-sample .

Push the Docker image to Docker Hub
- docker push your_dockerhub_username/aks-setup-sample

### 3. Create an AKS Cluster

Login to Azure
- az login

Create a resource group
- az group create --name aks-resource-group --location eastus

Create an AKS cluster
- az aks create --resource-group aks-resource-group --name aks-cluster --node-count 1 --enable-addons monitoring --generate-ssh-keys

Configure Kubectl
- az aks get-credentials --resource-group aks-resource-group --name aks-cluster

### 4. Deploy to AKS

Apply the deployment and service configuration
- kubectl apply -f deployment.yaml
- kubectl apply -f service.yaml

### 5. Access the Application

Get the external IP of the service
- kubectl get services
Access the application in your browser using the EXTERNAL-IP

## Clean up AKS Project

To delete the resources created in this project, run:
- az group delete --name aks-resource-group --yes --no-wait
