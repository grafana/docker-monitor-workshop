# Docker Monitoring Workshop with Grafana Alloy, Prometheus and Loki

The aim of this workshop is to provide a hands-on experience with monitoring Docker containers using Grafana Alloy, Prometheus and Loki. The workshop is divided into 4 parts:
- Part 1: Setting up the monitoring stack (Deploying Grafana Alloy, Prometheus and Loki)
- Part 2: Monitoring Docker Metrics (Use Alloy and cAdvisor to monitor Docker metrics)
- Part 3: Monitoring Docker Logs (Use Alloy to monitor Docker logs)
- Part 5: Building a custom Grafana dashboard (Combine metrics and logs in a custom Grafana dashboard)

## Prerequisites
- Docker
- Docker Compose
- Git
- curl

## Running the Demo

### Step 1: Clone the repository
```bash
git clone https://github.com/grafana/docker-monitor-workshop.git
```

### Step 2: Deploy the monitoring stack
```bash
cd docker-monitor-workshop
docker-compose up -d
```

### Step 3: Access Grafana Alloy UI
Open your browser and go to `http://localhost:12345`. This should show you a plank Alloy UI. 


### Configure Alloy to Monitor Docker Metrics

Take the class through building the Alloy config for metrics. Couple of fun facts:
- You can build an Alloy config from `right` to `left` (output to input) if you would like to show them the Alloy UI after each component is added to the config.
- Completed Alloy config can be found in `completed` folder.
- There are two ways to reload the Alloy config:
  - Restart the Alloy container
  - Use the `reload` API endpoint
    ```bash
    curl -X POST http://localhost:12345/-/reload
    ```

### Configure Alloy to Monitor Docker Logs
Same as above, but for logs.

### Building a custom Grafana dashboard

Both Explore Metrics and Explore Logs are preinstalled in the Grafana instance. The other option is to build a custom dashboard using the Grafana UI.

## Extra Data

Currently the workshop will monitor the containers deployed which most likely will be the Grafana Alloy, Prometheus and Loki containers. If you would like to make the workshop more interesting, you can deploy a few more containers and monitor them using Alloy. Included is the greenhouse microservices demo.

### Deploy the greenhouse microservices demo
```bash
docker compose -f "greenhouse/docker-compose-micro.yml" up -d --build
```

### Step 4: Bringing Deployment down

```bash
docker-compose down
```

Similarly for the greenhouse microservices demo:

```bash
docker compose -f "greenhouse/docker-compose-micro.yml" down
```


