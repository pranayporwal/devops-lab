\# Exercise 10: Multiple Kubernetes Applications and Replicas



\## Objective

Deploy two applications in Kubernetes using Deployments, replicas, and NodePort Services.



\## Prerequisites

\- Docker Desktop

\- Minikube

\- kubectl



\## Applications



\### Application 1: Nginx

\- Deployment: app1-nginx

\- Replicas: 3

\- Container Port: 80

\- Service: app1-nginx-svc

\- NodePort: 30001



\### Application 2: Echo Server

\- Deployment: app2-echo

\- Replicas: 2

\- Container Port: 8080

\- Service: app2-echo-svc

\- NodePort: 30002



\## Procedure



\### Step 1: Start Minikube

```bash

minikube start --driver=docker

```



\### Step 2: Deploy Nginx

```bash

kubectl apply -f app1-nginx.yaml

```



\### Step 3: Deploy Echo Server

```bash

kubectl apply -f app2-echo.yaml

```



\### Step 4: Verify Deployments

```bash

kubectl get deployments

```



\### Step 5: Verify Pods

```bash

kubectl get pods

```



\### Step 6: Verify Services

```bash

kubectl get services

```



\### Step 7: Access Nginx

```bash

minikube service app1-nginx-svc

```



\### Step 8: Access Echo Server

```bash

minikube service app2-echo-svc

```



\## Expected Results

\- The Nginx Deployment is configured for three replicas.

\- The Echo Server Deployment is configured for two replicas.

\- Both applications are exposed through NodePort Services.

\- Nginx displays its welcome page.

\- Echo Server returns a response when accessed.



Verify these results by running the commands above.



\## Configuration Files

\- `app1-nginx.yaml`: Nginx Deployment and Service configuration.

\- `app2-echo.yaml`: Echo Server Deployment and Service configuration.

\- `Exercise-10.1.jpg`: Exercise screenshot.



\## Cleanup

```bash

kubectl delete -f app1-nginx.yaml

kubectl delete -f app2-echo.yaml

```



\## Learning Outcomes

\- Understand Kubernetes Deployments and replicas.

\- Deploy multiple applications.

\- Expose applications using NodePort Services.

\- Inspect Pods, Deployments, and Services using kubectl.

