\# Exercise 3: Scaling Flask Application Using ReplicaSets



\## Objective

Deploy a Flask application on Kubernetes using a ReplicaSet, run multiple replicas, and expose the application through a Kubernetes Service.



\## Prerequisites

\- Docker Desktop

\- Minikube

\- kubectl

\- Python application source code

\- Dockerfile



\## Application Details

\- Application: Flash Sale Flask Application

\- Docker Image: flashsale:1.0

\- ReplicaSet: flashsale-rs

\- Number of Replicas: 3

\- Container Port: 5000

\- Service: flashsale-svc



\## Application Endpoints

\- `/` : Displays a welcome message and the Pod hostname.

\- `/buy` : Simulates a purchase and returns order information.

\- `/health` : Returns the health status and Pod hostname.



\## Procedure



\### Step 1: Start Minikube

Start the local Kubernetes cluster.



```bash

minikube start --driver=docker

```



\### Step 2: Build the Docker Image

Build the Flask application image using the Dockerfile.



```bash

docker build -t flashsale:1.0 .

```



\### Step 3: Load the Image into Minikube

Make the local image available to the Kubernetes cluster.



```bash

minikube image load flashsale:1.0

```



\### Step 4: Deploy the ReplicaSet and Service

Apply the Kubernetes configuration.



```bash

kubectl apply -f flashsale-replicaset.yaml

```



\### Step 5: Verify the ReplicaSet

Check the desired and available replicas.



```bash

kubectl get replicasets

```



\### Step 6: Verify the Pods

List the Pods created by the ReplicaSet.



```bash

kubectl get pods

```



\### Step 7: Verify the Service

Check the application Service.



```bash

kubectl get services

```



\### Step 8: Access the Application

Forward local port 8080 to the Service port 80.



```bash

kubectl port-forward service/flashsale-svc 8080:80

```



While port forwarding is running, open `http://localhost:8080/` in a browser.



The other endpoints can be accessed at:

\- `http://localhost:8080/buy`

\- `http://localhost:8080/health`



\### Step 9: Test Scaling

Scale the ReplicaSet to five replicas.



```bash

kubectl scale replicaset flashsale-rs --replicas=5

```



Verify the new replica count.



```bash

kubectl get replicasets

kubectl get pods

```



\### Step 10: Test Self-Healing

Delete one of the Pods created by the ReplicaSet.



```bash

kubectl delete pod <pod-name>

```



Replace `<pod-name>` with an actual Pod name from `kubectl get pods`.



Check the Pods again. The ReplicaSet should create a replacement to maintain the desired replica count.



\## Expected Results

\- The ReplicaSet is configured to maintain three replicas initially.

\- The Service routes requests to available application Pods.

\- The Flask endpoints return the expected application responses.

\- Scaling increases the desired replica count to five.

\- When a managed Pod is deleted, the ReplicaSet attempts to replace it.



Verify the actual results by executing the commands.



\## Configuration Files

\- `app.py`: Flask application source code.

\- `Dockerfile`: Instructions for building the Docker image.

\- `flashsale-replicaset.yaml`: ReplicaSet, health probes, and Service configuration.

\- `Exercise-3.1.jpg`, `Exercise-3.2.jpg`, and `Exercise-3.3.jpg`: Exercise screenshots.



\## Cleanup

Remove the Kubernetes resources created by this exercise.



```bash

kubectl delete -f flashsale-replicaset.yaml

```



\## Learning Outcomes

\- Understand ReplicaSets and Pod replicas.

\- Deploy and scale a containerized application.

\- Expose Pods through a Kubernetes Service.

\- Understand health probes and self-healing.

\- Inspect Kubernetes resources using kubectl.

