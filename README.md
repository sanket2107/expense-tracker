# Expense Tracker – Full Stack Application (Dockerized)

A **production-ready full-stack Expense Tracker application** built with **React, FastAPI, PostgreSQL**, containerized using **Docker**, automated with **GitHub Actions**, and deployed on **AWS EC2**.

This project demonstrates real-world **DevOps and cloud deployment practices** using Docker Compose and CI/CD pipelines.

---

## 🚀 Features

- Add and manage expenses
- RESTful API built with FastAPI
- Modern React frontend (Vite)
- PostgreSQL database with persistent storage
- Reverse proxy & routing using Traefik
- Health checks & auto-healing containers
- Separate development and production setups
- CI/CD pipelines for Docker image builds
- Cloud deployment on AWS EC2

---

## 🧰 Tech Stack

### Frontend
- React (Vite)
- Node.js
- Nginx (production)

### Backend
- Python 3.12
- FastAPI
- Uvicorn

### Database
- PostgreSQL

### DevOps & Cloud
- Docker & Docker Compose
- Traefik (reverse proxy)
- GitHub Actions (CI/CD)
- Docker Hub (image registry)
- AWS EC2 (deployment)

---

## 🏗️ Architecture Overview

User (Browser)
|
v
AWS EC2 (Port 80)
|
v
Traefik (Reverse Proxy)
|
|-----------|
| |
v v
Frontend Backend
(React) (FastAPI)
|
v
PostgreSQL DB


- `/` → Frontend
- `/api` → Backend
- Internal Docker network for service communication
- Database not exposed publicly

---

## 📂 Project Structure

expense-tracker/
│
├── frontend/
│ ├── Dockerfile
│ ├── nginx.conf
│ └── src/
│
├── backend/
│ ├── Dockerfile
│ ├── requirements.txt
│ └── app/
│
├── db/
│ └── *.sql
│
├── compose.yaml
├── compose.override.yaml
├── compose.prod.yaml
├── .github/workflows/
│ ├── docker-image.yml
│ └── backend.yml
└── README.md


---

## ⚙️ Docker Compose Setup

### 🔹 `compose.yaml`
Base services:
- Traefik
- PostgreSQL
- Shared volumes & networking

### 🔹 `compose.override.yaml` (Development)
- Hot reload for frontend & backend
- Local code mounted as volumes
- Fast development feedback loop

### 🔹 `compose.prod.yaml` (Production)
- Uses pre-built Docker Hub images
- Health checks & auto-healing
- Production-ready configuration

---

## 🔄 CI/CD with GitHub Actions

Two independent pipelines:

### Frontend Pipeline
- Triggers on `frontend/**` changes
- Builds Docker image
- Pushes image to Docker Hub

### Backend Pipeline
- Triggers on `backend/**` changes
- Builds FastAPI Docker image
- Pushes image to Docker Hub

---

## 🐳 Docker Hub Images

- **Frontend:**  
  https://hub.docker.com/repository/docker/sanket2122/expense-tracker

- **Backend:**  
  https://hub.docker.com/repository/docker/sanket2122/expense-tracker-backend

---

## 🚀 Running the Application

### Development

## docker compose up
Production
docker compose -f compose.yaml -f compose.prod.yaml up -d

🌐 Access the Application

Frontend: http://<EC2_PUBLIC_IP>/

Backend API: http://<EC2_PUBLIC_IP>/api

Traefik Dashboard: http://<EC2_PUBLIC_IP>:8080

📌 Key Learnings

Docker multi-stage builds

Compose file layering (base / dev / prod)

CI/CD automation with GitHub Actions

Container networking & routing

Production deployment on AWS

Debugging real-world Docker issues


👨‍💻 Author

Sanket Deshmukh
