---
title: Basic configuration
description: Quickly deploy minimal Prometheus and Grafana instances
---

Quickly deploy minimal Prometheus and Grafana instances. 

!!! note "As usual, this is for Debian using APT."

## Sources

- [Prometheus](https://prometheus.io/docs/prometheus/latest/getting_started/)
- [Prometheus - Grafana support for Prometheus](https://prometheus.io/docs/visualization/grafana/#grafana-support-for-prometheus)

## Requirements

None.

## Guide

### Prometheus basics

```title="Install Prometheus"
apt install prometheus
``` 

Check that there is at least one ` job_name` entry under ` scrape_configs` in `/etc/prometheus/prometheus.yml`. 

```title="Start Prometheus with its default config file"
cd /etc/prometheus/
./prometheus --config.file=prometheus.yml
```

Check that data is being served on [http://localhost:9100](http://localhost:9090). 

### Grafana basics

```title="Install Grafana"
apt install grafana
``` 

```title="Start grafana"
systemctl start grafana-server
```

The web interface should come online at [http://localhost:3000](http://localhost:3000). 
There, navigate the left menu to Connections > Data sources. 

Select "Add data source" and "Prometheus". 

Everything can be kept as default, the address of the Prometheus server is `http://localhost:9090` (and **not** `:9100`). 

Next, you can navigate to Explore > Metrics in the left menu and press "Let's start!". 
This should show every metric that was found on the prometheus server. 

!!! warning "Metrics refresh"
    I couldn't find how to refresh metrics. Once the initil connexion is done, I don't see a way to scan for aditional metrics or changes in the description of existing ones. 

    If you plan on adding aditional metrics, I recommend to do that before connecting Grafana. 

