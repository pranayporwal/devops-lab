# Exercise 5: Docker Security with AppArmor

## Objective
Secure a Dockerized Flask application using a custom AppArmor profile and verify that the security profile is attached to the container.

## Prerequisites
- Docker
- Python Flask application
- AppArmor-enabled Linux environment
- AppArmor utilities
- Docker AppArmor profile support

## Application Details
- Application: Flask
- Docker Image: flask-apparmor
- Container Name: flask-protected
- Application Port: 5000
- AppArmor Profile: my-apparmor-profile

## Procedure

### Step 1: Build the Docker Image

Build the Flask application image using the Dockerfile.

```bash
docker build -t flask-apparmor .
```

### Step 2: Load the AppArmor Profile

Load the custom profile into the Linux kernel.

```bash
sudo apparmor_parser -r -W my-apparmor-profile
```

### Step 3: Run the Secured Container

Start the application with the custom AppArmor profile.

```bash
docker run -d --name flask-protected --security-opt apparmor=my-apparmor-profile -p 5000:5000 flask-apparmor
```

### Step 4: Verify the Container

Check whether the container is running.

```bash
docker ps
```

### Step 5: Verify the Applied Security Profile

Inspect the container configuration.

```bash
docker inspect --format '{{json .HostConfig.SecurityOpt}}' flask-protected
```

### Step 6: Test the Application

Access the Flask application at:

http://localhost:5000

The application is expected to return:

Hello from AppArmor Secured Container!

## Expected Results

- The Flask application image builds successfully.
- The custom AppArmor profile loads successfully on a supported Linux host.
- The Docker container is started with the specified profile.
- The container configuration reports the requested security option.
- The application responds when its required permissions are allowed.

Verify these results by executing the commands in an AppArmor-enabled environment.

## Configuration Files

- `app.py`: Flask application source code.
- `Dockerfile`: Instructions for building the Docker image.
- `my-apparmor-profile`: AppArmor security rules.
- `Exercise-5.1.png`: Exercise screenshot.

## Cleanup

Stop and remove the container.

```bash
docker stop flask-protected
docker rm flask-protected
```

## Learning Outcomes

- Understand the purpose of AppArmor.
- Create a custom security profile.
- Apply AppArmor restrictions to a Docker container.
- Verify container security configuration.
- Understand how security restrictions can affect application execution.