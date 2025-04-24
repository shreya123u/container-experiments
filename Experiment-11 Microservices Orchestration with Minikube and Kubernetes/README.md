<h1>Microservices Orchestration with Minikube & Kubernetes</h1>
<br>This repository demonstrates how to deploy a microservices-based architecture using Minikube, Kubernetes, and Docker. It consists of an API Gateway and a Backend Service running inside a Minikube cluster.

<h2>Prerequisites</h2>
<br>Before you begin, ensure you have the following installed:<br><br>

<br>Minikube - For running a local Kubernetes cluster
<br>kubectl - For interacting with the Kubernetes cluster
<br>Docker - For building container images
<br>Project Structure<br>
.
├── README.md<br>
├── backend/<br>
│   ├── Dockerfile<br>
│   ├── backend.py<br>
│   └── requirements.txt<br>
├── api-gateway/<br>
│   ├── Dockerfile<br>
│   ├── api_gateway.py<br>
│   └── requirements.txt<br>
└── kubernetes/<br>
    ├── backend-service.yaml<br>
    └── api-gateway.yaml<br>

    

<h2>🔍 Architecture Overview</h2>
<br>Components
<br>API Gateway

<br>Acts as the entry point for all client requests
<br>Routes requests to appropriate backend services
<br>Port: 8080
<br>Backend Service

<br>Handles business logic
<br>Returns simple responses
<br>Port: 5000
<h3>🔁 Communication Flow</h3>
<br>1️⃣ Client → API Gateway (Port 8080)<br> 2️⃣ API Gateway → Backend Service (Port 5000) <br>3️⃣ Backend Service → API Gateway <br>4️⃣ API Gateway → Client

<h2>Happy coding! 🚀</h2>
