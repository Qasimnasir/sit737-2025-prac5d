# SIT737-2025-Prac5D – Arithmetic Microservice

## Overview

This project is part of the SIT737 Cloud-Native Application Development course. It implements an **Arithmetic Microservice** using **Node.js** and **Express.js**. The service performs basic arithmetic operations (add, subtract, multiply, divide), is **Dockerized**, and **published to Google Cloud's Container Registry** for cloud-based deployment.

---

## Microservice Features

| Endpoint | HTTP Method | Description |
|----------|-------------|-------------|
| `/health` | GET | Health check |
| `/add?num1=5&num2=2` | GET | Addition |
| `/subtract?num1=5&num2=2` | GET | Subtraction |
| `/multiply?num1=5&num2=2` | GET | Multiplication |
| `/divide?num1=5&num2=2` | GET | Division |

The service validates all numeric inputs and handles division-by-zero cases.

---

## Dockerization Instructions

### 1. Build Docker Image

```bash
docker build -t gcr.io/sit737-2025-prac5d-461316/arithmetic-service:v1 .
````

### 2. Authenticate with Google Cloud

```bash
gcloud auth login
gcloud config set project sit737-2025-prac5d-461316
gcloud auth configure-docker
```

### 3. Push Image to Google Container Registry

```bash
docker push gcr.io/sit737-2025-prac5d-461316/arithmetic-service:v1
```

### 4. Run the Image

```bash
docker run -p 3000:3000 gcr.io/sit737-2025-prac5d-461316/arithmetic-service:v1
```

Then open your browser and test the following:

* `http://localhost:3000/health`
* `http://localhost:3000/add?num1=5&num2=3`
* `http://localhost:3000/divide?num1=8&num2=0` (to test error handling)

---

## Local Testing with Docker Compose

You can also run the microservice using Docker Compose:

```bash
docker-compose up --build
```

---

## 🔗 Repository & Registry

* **GitHub Repo:** [https://github.com/Qasimnasir/sit737-2025-prac5d](https://github.com/Qasimnasir/sit737-2025-prac5d)
* **Container Image:** `gcr.io/sit737-2025-prac5d-461316/arithmetic-service:v1`
