\# Exercise 2: Deploy Flask Application on Minikube



\## Objective

Deploy a Python Flask application on Kubernetes using Minikube, Docker, kubectl, and a YAML configuration file.



\## Prerequisites

\- Docker Desktop

\- Minikube

\- kubectl

\- Python

\- Dockerfile and Flask application code



\## Application Details

\- Application: Flask

\- Docker Image: flask-app

\- Container Port: 15000

\- Kubernetes Deployment: flask-app

\- Kubernetes Service: flask-app-service



\## Procedure



\### Step 1: Start Minikube



Start the local Kubernetes cluster.



```bash

minikube start --driver=docker

```



\### Step 2: Build the Docker Image



Build the Flask application image from the Dockerfile.



```bash

docker build -t flask-app:latest .

```



Load the image into Minikube so Kubernetes can use the locally built image.



```bash

minikube image load flask-app:latest

```



\### Step 3: Deploy the Application



Apply the Kubernetes YAML configuration.



```bash

kubectl apply -f flask-deployment.yaml

```



\### Step 4: Verify the Deployment



Check the deployment status.



```bash

kubectl get deployments

```



\### Step 5: Verify the Pods



Check whether the Flask Pod is running.



```bash

kubectl get pods -l app=flask-app

```



\### Step 6: Inspect the Deployment



View detailed information about the Deployment and its events.



```bash

kubectl describe deployment flask-app

```



\### Step 7: Check Application Logs



Inspect the application logs.



```bash

kubectl logs deployment/flask-app

```



\### Step 8: Verify the Service



List the available Kubernetes Services.



```bash

kubectl get services

```



\### Step 9: Access the Application



Retrieve the URL for the Flask Service.



```bash

minikube service flask-app-service --url

```



Open the resulting URL in a browser to access the application.



\## Expected Result

The Flask application should return the message:



Hello from Flask on Kubernetes!



Verify the actual deployment and application response when executing the exercise.



\## Configuration Files

\- `app.py`: Flask application source code.

\- `Dockerfile`: Instructions for building the Docker image.

\- `flask-deployment.yaml`: Kubernetes Deployment and Service configuration.

\- `Exercise-2.1.jpg` and `Exercise-2.2.jpg`: Exercise screenshots.



\## Cleanup



Remove the deployed Kubernetes resources when finished.



```bash

kubectl delete -f flask-deployment.yaml

```



\## Learning Outcomes

\- Build a Docker image for a Python application.

\- Deploy a containerized application using Kubernetes.

\- Configure a Kubernetes Deployment using YAML.

\- Expose a Flask application through a Kubernetes Service.

\- Verify deployments, Pods, Services, and application logs.

