# SAP-Lite Monitoring Suite

A lightweight sim of how enterprise monitoring works in SAP-like environments. Using **Flask**, **Docker**, **Prometheus**, and **Grafana** to showcase application and database monitoring, log parsing, and DevOps basics.

## What you can do with it

- Simulate SAP-like log monitoring (bash script that scans mock log files for error patterns)
- Mock database health checks with Python (py script mimicking something like a monitor tool for checking states of dbs)
- See a data visualisation with a live dashboard built with Flask
- Launch the whole suite with one command (every component (Flask, Prometheus, and Grafana) runs in its own container)

## How to run the dummy app

### 1. Running it with [Docker](https://www.docker.com/products/docker-desktop)

After unzipping or cloning the repo, launch all services:

```bash
docker-compose up --build
```

And access the tools in your browser under:

- Flask Dashboard → http://localhost:5000
- Prometheus → http://localhost:9090
- Grafana → http://localhost:3000  (Login: admin / admin)


### 2. Running it without Docker

For this you need to run the dashboard manually

#### Req: 

- Python 3.10 or higher
- pip

Steps: 

```bash

# 1. Create a virtual environment
python -m venv venv
venv\\Scripts\\activate        # On Windows
source venv/bin/activate      # On Mac/Linux

# 2. Install Flask
pip install -r requirements.txt

# 3. Start the app
cd dashboard
python app.py
```

After that, open your browser at http://localhost:5000


## How to connect Grafana to Prometheus

1. When Grafana is up, go to http://localhost:3000 and log in
2. Click on "Configuration" and from there "Data Sources"
3. Click "Add data source" and select Prometheus
4. Set the URL to: http://prometheus:9090
5. Click "Save & Test"

It should be set up to create dashboards.

## Structure

```sql
sap-lite-monitoring-suite/
├── ansible/               → Automation (WIP)
├── dashboard/             → Flask app + HTML dashboard
├── docker/                → Dockerfile for Flask
├── docs/                  → Architecture & documentation
├── mock_data/             → Simulated logs (SAP-style)
├── monitoring/            → Prometheus + Grafana config
├── scripts/               → Log and DB health check scripts
├── docker-compose.yml     → One-click orchestration
├── requirements.txt       → Flask dependency
├── gitignore.txt
├── LICENSE.txt
└── README.md
```
