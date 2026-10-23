\# Exercise 4: Docker Networking with Multiple Containers



\## Objective

Create a custom Docker bridge network and run a Flask web application, MySQL database, and Redis cache in separate containers. Verify that the containers can communicate over the same network.



\## Prerequisites

\- Docker Desktop

\- Python Flask application

\- Dockerfile

\- requirements.txt



\## Application Details

\- Flask API: Port 5001

\- MySQL: Port 3306

\- Redis: Port 6379

\- Docker Network: my-bridge-net

\- Docker Image: flask-api



\## Procedure



\### Step 1: Create a Docker Bridge Network



Create a custom network for the containers.



```bash

docker network create --driver bridge my-bridge-net

```



Verify the network:



```bash

docker network ls

docker network inspect my-bridge-net

```



\### Step 2: Build the Flask Docker Image



Build an image using the Dockerfile.



```bash

docker build -t flask-api .

```



Verify the image:



```bash

docker images

```



\### Step 3: Start the MySQL Container



Start MySQL on the custom network. The password below is for this local lab only.



```bash

docker run -d --name mysql --network my-bridge-net -e MYSQL\_ROOT\_PASSWORD=labroot123 mysql:latest

```



\### Step 4: Start the Redis Container



```bash

docker run -d --name redis --network my-bridge-net redis:latest

```



\### Step 5: Start the Flask Container



Publish port 5001 so the application can be accessed from the host machine.



```bash

docker run -d --name flask --network my-bridge-net -p 5001:5001 flask-api

```



\### Step 6: Verify the Containers



```bash

docker ps

```



Check that the Flask, MySQL, and Redis containers are running.



\### Step 7: Test the Flask Application



Access the API endpoint in a browser or HTTP client.



```text

http://localhost:5001/about

```



The endpoint should return JSON containing the application's name, version, and description.



\### Step 8: Test Container Connectivity



Test whether the Flask container can resolve the other container names.



```bash

docker exec flask ping -c 3 mysql

docker exec flask ping -c 3 redis

```



If `ping` is unavailable inside the Flask container, install the utility in the Dockerfile or use another suitable connectivity test.



\### Step 9: Inspect the Docker Network



```bash

docker network inspect my-bridge-net

```



Verify that the three containers are attached to the network.



\## Expected Results



\- The custom bridge network is created successfully.

\- The Flask, MySQL, and Redis containers join the network.

\- The Flask API returns the expected JSON response when accessible.

\- Container names resolve over the user-defined bridge network.



Verify these results by executing the commands.



\## Configuration Files



\- `app.py`: Flask API source code.

\- `Dockerfile`: Instructions for building the Flask image.

\- `requirements.txt`: Python package dependencies.

\- `Exercise-4.1.jpg`, `Exercise-4.2.jpg`, `Exercise-4.3.jpg`, and `Exercise-4.4.jpg`: Exercise screenshots.



\## Cleanup



Stop and remove the containers.



```bash

docker stop flask mysql redis

docker rm flask mysql redis

```



Remove the network.



```bash

docker network rm my-bridge-net

```



\## Learning Outcomes



\- Create and inspect a Docker bridge network.

\- Build and run a Docker image.

\- Connect multiple containers to one network.

\- Understand container name resolution.

\- Publish a container port to the host machine.

