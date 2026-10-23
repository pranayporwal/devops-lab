\# Exercise 9: Jenkins Multi-Stage Pipeline



\## Objective

Create a Jenkins pipeline to build, test, and deploy a Python Flask application. The pipeline also runs the application and verifies its response.



\## Prerequisites

\- Docker Desktop

\- Jenkins

\- Git

\- Python application files

\- Jenkins Pipeline support



\## Project Files

\- `app.py`: Flask application source code.

\- `Dockerfile`: Builds the application image.

\- `requirements.txt`: Specifies Python dependencies.

\- `test\_app.py`: Contains unit tests for the Flask application.

\- `Jenkinsfile`: Defines the multi-stage Jenkins pipeline.

\- `Exercise-9.1.png`: Jenkins console output screenshot.



\## Application Details

\- Application: Flask

\- Docker Image: `exercise9-app`

\- Container Name: `exercise9-flask`

\- Application Port: 5000



\## Procedure



\### Step 1: Create the Flask Application

The Flask application responds to requests at the root endpoint `/` with a greeting message.



\### Step 2: Define Dependencies

The `requirements.txt` file specifies the Flask and Werkzeug versions required by the application.



\### Step 3: Create Unit Tests

The `test\_app.py` file tests the root endpoint and checks the HTTP response status and message.



\### Step 4: Build the Application

The Jenkins pipeline builds the Docker image using the Dockerfile.



```bash

docker build -t exercise9-app .

```



\### Step 5: Run Unit Tests

The pipeline runs the unit tests inside a temporary Docker container.



```bash

docker run --rm --entrypoint python exercise9-app -m unittest test\_app.py

```



\### Step 6: Deploy the Application

The pipeline creates a mock deployment directory and copies the application source file and dependency list into it.



\### Step 7: Run the Application

The pipeline starts a Docker container named `exercise9-flask` using the built image.



\### Step 8: Test the Deployed Application

The pipeline sends an HTTP request to the application's root endpoint and checks whether the returned message matches the expected text.



\### Step 9: Pipeline Completion

The Jenkins pipeline reports success or failure based on the execution of its stages and performs container cleanup afterward.



\## Expected Results

\- The Docker image builds successfully.

\- The unit tests pass.

\- The application files are copied into the mock deployment directory.

\- The Flask application starts in a container.

\- The HTTP response matches the expected message.

\- Jenkins reports the pipeline result in the console output.



Verify these results by running the pipeline in Jenkins.



\## Configuration Files

\- `app.py`: Flask application.

\- `Dockerfile`: Docker image build instructions.

\- `requirements.txt`: Python dependencies.

\- `test\_app.py`: Automated unit tests.

\- `Jenkinsfile`: Build, Test, Deploy, Run Application, and Test Application stages.



\## Cleanup

The Jenkins pipeline includes a post-build action to remove the application container.



\## Learning Outcomes

\- Understand continuous integration and pipeline automation.

\- Build Docker images through Jenkins.

\- Execute automated unit tests.

\- Deploy and run a containerized application.

\- Verify application behavior through HTTP requests.

\- Interpret Jenkins pipeline logs and build results.

