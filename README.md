# skill-test-2
https://github.com/mohanDevOps-arch/Blue-green-Deployment.git

Blue-Green Deployment with Kubernetes and Docker

Overview

This project demonstrates a Blue-Green Deployment strategy using Kubernetes and Docker. It ensures zero downtime during application updates by running two versions (Blue & Green) and switching traffic seamlessly.

Project Structure

Docker Images: Built and uploaded Docker images for 3 services.

Kubernetes Manifests:

Deployments (deployment.yaml)

Services (service.yaml)

Ingress (if applicable)

Application Access: Exposed the app using a Kubernetes Service.

Technologies Used

Docker: To containerize the application services.

Kubernetes: For deployment and service management.

Blue-Green Strategy: Ensures smooth version switching.

Setup Instructions

1. Clone the Repository

git clone https://github.com/shivamsonari376/Blue-green-Deployment.git
cd Blue-green-Deployment

2. Build & Push Docker Images

Replace <your-dockerhub-username> with your actual Docker Hub username.

docker build -t <your-dockerhub-username>/service1:latest ./service1

docker build -t <your-dockerhub-username>/service2:latest ./service2

docker build -t <your-dockerhub-username>/service3:latest ./service3

docker push <your-dockerhub-username>/service1:latest
docker push <your-dockerhub-username>/service2:latest
docker push <your-dockerhub-username>/service3:latest

3. Deploy to Kubernetes

Apply the Kubernetes manifests:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

4. Verify Deployments

Check if pods are running:

kubectl get pods

Check the services:

kubectl get svc

5. Access the Application

Find the LoadBalancer/NodePort IP:

kubectl get svc

Then, open the IP in a browser:

http://<service-ip>:<port>

6. Switching Traffic (Blue-Green Deployment)

Deploy the Green version alongside Blue.

Update the service to route traffic to Green.

Once verified, remove the Blue deployment.

kubectl set image deployment/service1 service1=<your-dockerhub-username>/service1:new-version
kubectl rollout status deployment/service1

Future Improvements

Implement Canary Deployments

Add CI/CD pipeline for automated deployments

Author

Shivam Sonari📧 shivamsonari376@gmail.com
