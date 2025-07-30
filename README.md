### 📦 Kubernetes with Minikube — Getting Started Project
This project is a hands-on exploration of key Kubernetes concepts using Minikube. It includes deploying an Nginx web server, creating services, and working with ConfigMaps and Secrets — all managed through declarative YAML files

### 🚀 What I hope to Learn
- How to set up a Kubernetes cluster locally with Minikube
- Create and manage Deployments and Pods
- Expose applications using Services
- Use ConfigMaps for non-sensitive data
- Store and inject sensitive data using Secrets
- Write Kubernetes configurations in YAML
- Document your DevOps journey professionally using GitHub

### 📁 Project Structure
├── nginx-deployment.yaml     # Deployment file for Nginx web server
├── nginx-service.yaml        # Service to expose the Nginx deployment
├── README.md                 # Project documentation

### ⚙️ Setup Instructions
1. Install prerequisites:
- Minikube
- Kubectl
2.  Start Minikube:
- minikube start
- kubectl get nodes
3. Apply Deployment:
- kubectl apply -f nginx-deployment.yaml
- kubectl get deployments
4. Apply Service
- kubectl apply -f nginx-service.yaml
- kubectl get svc
- minikube service nginx-service

### 🔍 Breakdown of nginx-deployment.yaml
- **apiVersion** (string): `apps/v1`
- **kind** (string): `Deployment`
- **metadata** (object):
  - **name** (string): `nginx-deployment`
- **spec** (object):
  - **replicas** (number): `2`
  - **selector** (object):
    - **matchLabels** (object):
```json
{
  "app": "nginx"
}
```

  - **template** (object):
    - **metadata** (object):
```json
{
  "labels": {
    "app": "nginx"
  }
}
```

    - **spec** (object):
```json
{
  "containers": [
    {
      "name": "nginx",
      "image": "nginx:latest",
      "ports": [
        {
          "containerPort": 80
        }
      ]
    }
  ]
}
```
### 💡 This creates two Nginx pods, manages them via a Deployment controller, and opens port 80.

### 🌐 Breakdown of nginx-service.yaml
- **apiVersion** (string): `v1`
- **kind** (string): `Service`
- **metadata** (object):
  - **name** (string): `nginx-service`
- **spec** (object):
  - **selector** (object):
    - **app** (string): `nginx`
  - **ports** (array):
    - Item 1:
```json
{
  "protocol": "TCP",
  "port": 80,
  "targetPort": 80
}
```

  - **type** (string): `NodePort`

### 🌐 This exposes the Nginx pods to your local machine using a NodePort. You can view the service in your browser using:
- minikube service nginx-service
### 💬 Reflections
“This project helped me understand how Kubernetes abstracts infrastructure complexity. The declarative nature of YAML and the power of kubectl commands made it easier to manage containerized applications.” — Obioma
