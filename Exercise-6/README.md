\# Exercise 6: Real-Time Monitoring and Alerting



\## Objective

Develop a real-time monitoring system for a quick-commerce delivery application using Python, Prometheus, Grafana, Docker, and Jenkins.



\## Prerequisites

\- Docker Desktop

\- Python 3.10 or higher

\- Prometheus

\- Grafana

\- Jenkins

\- Python Prometheus client library



\## Project Files

\- `delivery\_metrics.py`: Generates simulated delivery metrics.

\- `prometheus.yml`: Configures Prometheus metric collection.

\- `alert\_rules.yml`: Defines alert conditions.

\- `Dockerfile`: Builds the delivery metrics application image.

\- `JenkinsDockerfile`: Defines the Jenkins Docker image configuration.

\- `Jenkinsfile`: Defines the Jenkins automation pipeline.

\- `Exercise-6.1.png`, `Exercise-6.2.png`, and `Exercise-6.3.png`: Exercise screenshots.



\## Procedure



\### Step 1: Install the Python Dependency



Install the Prometheus client library.



```bash

python -m pip install prometheus-client

```



\### Step 2: Run the Delivery Metrics Application



Start the Python application.



```bash

python delivery\_metrics.py

```



The application generates simulated delivery metrics, including total deliveries, pending deliveries, deliveries on the way, and average delivery time.



\### Step 3: Verify the Metrics Endpoint



Open the metrics endpoint in a browser.



http://localhost:8000/metrics



The endpoint exposes application metrics in Prometheus format.



\### Step 4: Configure Prometheus



Configure Prometheus using `prometheus.yml` to scrape application metrics and load the alert rules from `alert\_rules.yml`.



Start Prometheus with the configuration files mounted into its container.



```bash

docker run -d --name prometheus -p 9090:9090 -v ./prometheus.yml:/etc/prometheus/prometheus.yml -v ./alert\_rules.yml:/etc/prometheus/alert\_rules.yml prom/prometheus

```



Access the Prometheus interface:



http://localhost:9090



Navigate to \*\*Status → Targets\*\* to inspect the configured scrape targets.



\### Step 5: Configure Alert Rules



The `alert\_rules.yml` file defines alerts for high pending deliveries and high average delivery time.



Prometheus evaluates these rules against the collected application metrics.



\### Step 6: Start Grafana



Run Grafana using Docker.



```bash

docker run -d --name grafana -p 3000:3000 grafana/grafana

```



Access Grafana:



http://localhost:3000



The default credentials for a fresh Grafana installation are:



\- Username: `admin`

\- Password: `admin`



Follow the setup prompts if they appear.



\### Step 7: Configure the Prometheus Data Source



In Grafana, navigate to the data sources section and add Prometheus.



Configure the URL using the address at which Grafana can reach Prometheus, then select \*\*Save \& Test\*\*.



\### Step 8: Create the Monitoring Dashboard



Create dashboard panels for the following metrics:



1\. Total Deliveries — `total\_deliveries`

2\. Pending Deliveries — `pending\_deliveries`

3\. On-the-Way Deliveries — `on\_the\_way\_deliveries`

4\. Average Delivery Time — `average\_delivery\_time\_sum / average\_delivery\_time\_count`



Use the dashboard to observe the simulated delivery activity.



\### Step 9: Configure Jenkins Automation



Use the supplied `Jenkinsfile` to configure the Jenkins pipeline for the monitoring application.



The pipeline describes the stages for checking Docker, preparing the workspace, building the application image, and starting the monitoring services.



Configure the Jenkins environment and required file paths before running the pipeline.



\### Step 10: Simulate Alerts



Modify the pending delivery values in `delivery\_metrics.py` to exceed the configured threshold.



Restart the metrics application if necessary, then inspect the Prometheus alerts interface and Grafana to observe the alert conditions.



\## Expected Results



\- The Python application exposes delivery metrics.

\- Prometheus collects metrics from the configured target.

\- Grafana displays delivery monitoring dashboards.

\- Prometheus evaluates the configured alert rules.

\- Jenkins provides a pipeline for automating the monitoring setup.



Actual results should be recorded after executing and verifying the relevant steps.



\## Cleanup



Stop and remove the monitoring containers when they are no longer needed.



```bash

docker stop prometheus grafana

docker rm prometheus grafana

```



Stop the delivery metrics application using `Ctrl+C` if it is running in the foreground.



\## Learning Outcomes



\- Expose application metrics using Python.

\- Configure Prometheus to scrape metrics.

\- Create monitoring dashboards with Grafana.

\- Define alert rules for operational conditions.

\- Understand how Jenkins can automate monitoring infrastructure.

