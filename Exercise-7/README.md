\# Exercise 7: Jenkins CI Automation for Delivery Monitoring



\## Objective

Set up a delivery monitoring application using Python, Prometheus, and Grafana, and use Jenkins to automate the monitoring pipeline.



\## Prerequisites

\- Docker Desktop

\- Python

\- Jenkins

\- Prometheus

\- Grafana

\- Git



\## Project Files

\- `delivery\_metrics.py`: Generates simulated delivery metrics.

\- `prometheus.yml`: Configures Prometheus metric collection.

\- `alert\_rules.yml`: Defines alerting conditions.

\- `Dockerfile`: Builds the delivery metrics application image.

\- `JenkinsDockerfile`: Defines the Jenkins container image configuration.

\- `Jenkinsfile`: Defines the Jenkins pipeline stages.

\- `Exercise-7.1.png`: Jenkins dashboard screenshot.

\- `Exercise-7.2.png`: Delivery monitoring pipeline screenshot.

\- `Exercise-7.3.png`: Jenkins console output screenshot.

\- `Exercise-7.4.png`: Jenkins console output screenshot.



\## Procedure



\### Step 1: Install the Python Dependency



Install the Prometheus client library.



```bash

python -m pip install prometheus-client

```



\### Step 2: Run the Metrics Application



Start the Python application.



```bash

python delivery\_metrics.py

```



\### Step 3: Verify Application Metrics



Access the metrics endpoint.



http://localhost:8000/metrics



The endpoint should expose the delivery metrics in Prometheus format.



\### Step 4: Configure Prometheus



Use `prometheus.yml` to configure the metrics scrape targets and `alert\_rules.yml` to configure alert rules.



Start Prometheus with the configuration files mounted into the container. Ensure the configured target is reachable from Prometheus.



Prometheus interface:



http://localhost:9090



Check the configured targets under Status → Targets.



\### Step 5: Configure Grafana



Start Grafana using Docker and access the interface.



http://localhost:3000



Configure Prometheus as a data source using the address reachable from the Grafana container. Save and test the connection.



\### Step 6: Configure the Jenkins Pipeline



Use the supplied `Jenkinsfile` to configure the delivery monitoring pipeline in Jenkins.



The pipeline defines automation for preparing the workspace, building the application image, running the application, and starting the monitoring services.



Ensure Docker and the required files are available to the Jenkins execution environment before running the pipeline.



\### Step 7: Verify the Pipeline



Run the Jenkins pipeline and review the stage results and console output.



Record the actual build status after execution.



\### Step 8: Verify Monitoring and Alerts



Check the Prometheus targets, inspect the available metrics, and review the configured alert rules.



Use Grafana to visualize the delivery metrics and verify the monitoring dashboard.



\## Expected Results



\- The application exposes delivery metrics.

\- Prometheus collects metrics from its configured targets.

\- Grafana provides a dashboard for delivery monitoring.

\- Jenkins runs the configured pipeline stages.

\- Alert rules identify delivery conditions that exceed configured thresholds.



Verify these results by executing the relevant steps.



\## Learning Outcomes



\- Understand application metrics and monitoring.

\- Configure Prometheus scrape targets and alert rules.

\- Visualize metrics using Grafana.

\- Define an automation pipeline using Jenkins.

\- Review Jenkins build logs and pipeline results.

