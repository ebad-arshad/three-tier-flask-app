# Three-Tier Flask Application with MySQL

A simple three-tier web application built with Flask and MySQL, containerized with Docker, and deployable to Kubernetes.
This project demonstrates how a backend application (Flask) communicates with a database (MySQL).

# Features

Flask-based web frontend for form submission and data display

MySQL database for persistent storage

Dockerized using lightweight Alpine images

Optional Kubernetes deployment for orchestration and scaling

Persistent data using Docker Volumes or Kubernetes PVCs

## Run with Docker Compose

Clone the Repository

```bash
git clone https://github.com/ebad-arshad/three-tier-flask-app.git &&
cd three-tier-flask-app
```

## Start the Containers

```python
docker-compose up --build
```
This will:

Start a MySQL database container.

Start the Flask application container linked to MySQL.

Once both services are running, open your browser at:
**http://localhost:8080**
## Environment Variables

The app reads database credentials from environment variables set in the docker-compose.yml file:

**MYSQL_ROOT_PASSWORD**\
**MYSQL_DATABASE**\
**MYSQL_USER**\
**MYSQL_PASSWORD**

## Stop and Remove Containers
Press Ctrl + C in the terminal running Docker Compose,
or run this command from another terminal:

```
docker-compose down
```
To also remove volumes (all saved data):
```
docker-compose down -v
```

# Run on Kubernetes
Apply the Deployments and Services
```
kubectl apply -f deployment.yaml &&
kubectl apply -f service.yaml &&
kubectl apply -f mysql-storage.yaml
```
Port Forward the Flask App

```
kubectl port-forward --address 0.0.0.0 svc/three-tier-flask-app 8080:8080
```
Then open **http://localhost:8080** in your browser.

# Clean Up Kubernetes Resources

```
kubectl delete -f deployment.yaml &&
kubectl delete -f service.yaml &&
kubectl delete -f mysql-storage.yaml
```

# Summary

**This project demonstrates how to:**

Build and run multi-container apps with Docker

Connect services using internal Docker/K8s networking

Use volumes for database persistence 

Deploy and manage apps using Kubernetes manifests
