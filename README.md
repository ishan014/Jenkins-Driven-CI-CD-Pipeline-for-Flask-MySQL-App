## Architecture

┌──────────────────────────────┐
│        User Browser          │
│        Port: 5000            │
└───────────────┬──────────────┘
                │ HTTP Request
                ▼
┌──────────────────────────────┐
│     Flask App Container      │
│  Service: flask              │
│  Image: flask-app            │
│                              │
│  - Flask Web Application     │
│  - Reads DB env variables    │
└───────────────┬──────────────┘
                │ SQL over Docker Network
                ▼
┌──────────────────────────────┐
│     MySQL DB Container       │
│  Service: mysql              │
│  Database: devops            │
│                              │
│  - messages table            │
│  - Persistent volume         │
└───────────────┬──────────────┘
                │
                ▼
┌──────────────────────────────┐
│     Docker Host / EC2        │
│  - Docker Engine             │
│  - Docker Compose            │
│  - Jenkins (CI/CD)           │
└──────────────────────────────┘



🔹 Architecture Highlights

Client Layer: User accesses the app via browser on port 5000

Application Layer: Flask app running inside a Docker container

Database Layer: MySQL container with persistent storage

Networking: Private Docker network for secure container communication

Automation: Jenkins handles build & deployment

⭐ Project Overview

Application Tier:

Python Flask web app to submit and view messages

Database Tier:

MySQL database to store messages persistently

Orchestration:

Docker Compose manages multi-container setup

CI/CD:

Jenkins pipeline automates build and deployment

✅ Ideal DevOps portfolio project to showcase containerization, orchestration, and CI/CD skills.

🎯 Project Objectives

Build a simple two-tier web application

Containerize Flask and MySQL using Docker

Manage services using Docker Compose

Implement Jenkins CI/CD pipeline to:

Clone GitHub repo

Build Docker image

Deploy containers automatically

🧩 Key Features
🔹 Flask Application

Web interface to submit messages

Fetches and displays stored messages

Uses environment variables for DB config

Auto-creates messages table if not present

🔹 MySQL Database

Runs as a separate container

Uses devops database (configurable)

Data persists via named Docker volume

Health check ensures DB readiness

🔹 CI/CD Pipeline (Jenkins)

Declarative Jenkinsfile

Fresh Docker image build on every run

Zero-downtime redeployment using Docker Compose

🛠 Tech Stack

Backend: Python, Flask

Database: MySQL

Containers: Docker, Docker Compose

CI/CD: Jenkins

Version Control: GitHub

📂 Project Structure

app.py – Flask routes, DB connection, DB initialization

templates/ – HTML files for UI

docker-compose.yml – Flask + MySQL services, volumes, healthchecks

Dockerfile – Flask app image definition

Jenkinsfile – CI/CD pipeline stages

requirements.txt – Python dependencies

2-tier Output.png – App output screenshot (optional)

🏗 Application Architecture

Flask app exposes port 5000

Flask communicates with MySQL over Docker network

MySQL data stored in mysql-data volume

Environment variables used:

MYSQL_HOST

MYSQL_USER

MYSQL_PASSWORD

MYSQL_DB



⚙️ End-to-End Workflow

Developer pushes code to GitHub

Jenkins pipeline triggers

Jenkins:

Clones repository

Builds Flask Docker image

Stops existing containers

Deploys updated stack

Docker Compose:

Starts MySQL and waits for health check

Starts Flask app with DB environment variables

User accesses app on http://<server-ip>:5000

🔑 Environment Configuration

Configured in docker-compose.yml:

MYSQL_HOST → MySQL service name

MYSQL_USER → DB user

MYSQL_PASSWORD → DB password

MYSQL_DB → Database name

Flask reads values using:

os.environ.get()

🚀 Running the Application (High-Level)
Without Jenkins

Install Docker & Docker Compose

Clone the repository

Build and run using Docker Compose

Open browser → http://localhost:5000

With Jenkins

Install Jenkins on Docker-enabled host

Create a Pipeline job using this repo

Use provided Jenkinsfile

Trigger builds manually or via GitHub webhook

🔁 Jenkins CI/CD Pipeline Summary
Pipeline Stages

1️⃣ Clone Code

Pulls latest code from GitHub

2️⃣ Build Docker Image

Builds flask-app:latest

3️⃣ Deploy with Docker Compose

Stops old containers

Starts updated Flask + MySQL stack

📌 Jenkins agent itself acts as the deployment server → simple & effective DevOps setup



Interview-friendly & easy to explain live

Perfect for DevOps Fresher roles
