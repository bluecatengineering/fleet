# Service Point Monitoring

This monitoring solution is built on open source:

* prometheus collects metrics from the SPv4 Telemetry API metrics endpoint

* grafana is used to visualize the data.

Documentation for the SPv4 Telemetry API metrics endpoint is at [Edge API Guide for /api/v1/metrics](https://docs.bluecatnetworks.com/r/DNS-Edge-API-Guide/api/v1/metrics/Service-Point-v4.x.x)

Instructions for installing Prometheus and Grafana are here - [How to Install and Configure Prometheus and Grafana on Ubuntu](https://www.linode.com/docs/guides/how-to-install-prometheus-and-grafana-on-ubuntu/)

## Installation

Start by installing prometheus according to the documentation link provided above.

Next, customize your `/etc/prometheus/prometheus.yml` configuration file following the example `prometheus.yml` in this directory and then restart your prometheus daemon. Prometheus will poll the metrics endpoint on each specified service point and save those metrics in its embedded time-series database.

Next, install grafana according to the documentation link provided above and then import the 2 Grafana dashboards (json files) in the current directory.

## Dashboards

The **Edge Service Points Overview** dashboard gives a high-level view of every SP being monitored. We can see graphs of CPU and Memory utilization, root and /var partition usage, DRS QPS and DRS Query Logging (firehose).

The **Edge Service Point Details** dashboard gives a deeper view of individual SPs. The top row shows the current state of the SP at a glance; 5-minute load average, CPU, Memory, Swap, root FS, /var FS, Current DRS QPS (UDP & TCP) and DRS Max Live Queries.

Below that we have graphs for a more detailed breakdown of key metrics; CPU usage, network interfaces, DRS requests, DRS response types, memory usage, DRS query logging, malicious DNS queries, DRS live message count and a count of the various types of DRS policy objects., We can see graphs of CPU and Memory utilization, root and /var partition usage, DRS QPS and DRS Query Logging (firehose).
If you select multiple items from the host selector, the metrics from each SP will be shown in a list.

