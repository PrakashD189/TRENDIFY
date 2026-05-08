This project demonstrates a complete DevOps pipeline to deploy a production-ready web application using modern tools and cloud services.

The application is a pre-built React application (dist/ folder) deployed using:

Docker (Containerization)
Jenkins (CI/CD Automation)
DockerHub (Image Registry)
AWS EKS (Kubernetes Cluster)
Kubernetes (Deployment & Service)
GitHub (Version Control)
Architecture
GitHub → Jenkins → Docker → DockerHub → AWS EKS → LoadBalancer → Browser

Step-by-Step Setup
🔹 1. Clone Repository
git clone https://github.com/PrakashD189/TRENDIFY.git
cd TRENDIFY
🔹 2. Docker Setup
Build Image
docker build -t trendify-app .
Run Container
docker run -d -p 80:80 trendify-app
🔹 3. Push Image to DockerHub
docker tag trendify-app <dockerhub-username>/trendify-app
docker push <dockerhub-username>/trendify-app
🔹 4. Jenkins Setup
Install Jenkins
Install plugins:
Docker
Git
Pipeline
Kubernetes
Configure Pipeline:
Select Pipeline script from SCM
Add GitHub repository
Use Jenkinsfile
🔹 5. Kubernetes (EKS Setup)
Create Cluster
eksctl create cluster --name trendify-cluster --region ap-south-1
Verify
kubectl get nodes
🔹 6. Deployment
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
🔹 7. Access Application
kubectl get svc

Open the EXTERNAL-IP in browser.

 **CI/CD Pipeline Flow**

Jenkins Pipeline Stages:

Clone Code (auto via SCM)
Build Docker Image
Tag Image
Push to DockerHub
Deploy to Kubernetes
Kubernetes Configuration
Deployment
2 replicas
Uses Docker image from DockerHub
Rolling update strategy
Service
Type: LoadBalancer
Exposes app publicly via AWS ELB
**Monitoring**

Can be integrated using:

Prometheus
Grafana
**Security Notes**
Avoid hardcoding AWS credentials
Use IAM Roles for production
Store secrets in Jenkins Credentials

URL:URL: http://a18ed7c93fb1f491389dca1d8ddbff76-1270574876.ap-south-1.elb.amazonaws.com/

Push to DockerHub
Deploy to Kubernetes
