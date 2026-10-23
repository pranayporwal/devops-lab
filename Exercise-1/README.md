\# Exercise 1: Kubernetes Hello Pod



\## Objective

Deploy an Nginx container in Kubernetes, expose it through a NodePort Service, and access it using a web browser.



\## Prerequisites

\- Docker Desktop

\- Minikube

\- kubectl



\## Procedure



\### Step 1: Start Minikube



Start the local Kubernetes cluster.



```bash

minikube start

```



\### Step 2: Create a Kubernetes Pod



Create a Pod named `hello-k8s` using the Nginx container image.



```bash

kubectl run hello-k8s --image=nginx --port=80

```



\### Step 3: Verify the Pod



Check whether the Pod is running.



```bash

kubectl get pods

```



\### Step 4: Expose the Pod as a Service



Create a NodePort Service to make the application accessible.



```bash

kubectl expose pod hello-k8s --type=NodePort --port=80

```



\### Step 5: Access the Application



Open the application using Minikube.



```bash

minikube service hello-k8s

```



\## Expected Result



The Nginx welcome page should appear in the browser when the Pod and Service are running successfully.



\## Cleanup



Remove the Service and Pod after completing the exercise.



```bash

kubectl delete service hello-k8s

kubectl delete pod hello-k8s

```



\## Learning Outcomes



\- Understand Kubernetes Pods.

\- Create and inspect Pods using kubectl.

\- Expose an application using a NodePort Service.

\- Access an application deployed on Minikube.

