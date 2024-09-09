# System Monitoring with Node Exporter


## Project Overview

This project sets up a system monitoring stack using Node Exporter, Prometheus, and Grafana, all managed through Portainer. The goal is to collect and visualize hardware and OS metrics, including performance monitoring.

## Project Components
1. **Node Exporter**
    - **Purpose:** Collects hardware and OS metrics such as CPU, memory, disk usage, and network statistics.

2. **Prometheus**
    - **Purpose:** A monitoring and alerting toolkit that scrapes metrics from configured targets.
    
3. **Grafana**
    - **Purpose:** A data visualization and monitoring tool that visualizes the metrics collected by Prometheus.

## Step 1: Run Portainer into Docker
       docker run -d -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ee:2.21.0


## Step 2: Run Prometheus in Docker
 - Create Prometheus Volume:
        docker volume create prometheus_data
 - Start Prometheus:
         docker run -d --name prometheus-docker -p 9090:9090   --mount type=bind,source="$(pwd)/prometheus.yml",target=/etc/prometheus/prometheus.yml  --network monitoring_default prom/prometheus

## Step 3: Run Grafana in Docker
 - Create Grafana Volume:
         docker volume create grafana_da
 -  Start Grafana:
        docker run -d --name grafana-docker -p 3000:3000 -v grafana_data:/var/lib/grafana --network monitoring_default grafana/grafana

## Check Node Exporter is up and running 

## Access Grafana
    Open your web browser and navigate to http://localhost:3000.
    Default credentials: admin / admin

## Configure Grafana
    Add Prometheus as a data source.
    Create dashboards to visualize metrics.





    