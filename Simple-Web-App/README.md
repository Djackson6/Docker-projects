# 🚀 Simple Web App Deployment with Docker & Nginx

This project demonstrates how to **deploy a simple static web application** using **Docker** and **Nginx**.
The application serves an `index.html` page through an Nginx container built from a custom Dockerfile.

The purpose of this project is to showcase **core Docker fundamentals** used in real-world DevOps and cloud environments.

---

## 🧠 Project Overview

**What this project does:**

* Uses Nginx as a web server
* Serves a static `index.html` file
* Builds a custom Docker image
* Runs the application inside a container

This project is intentionally simple to focus on **Docker workflow and fundamentals**.

---

## 📂 Project Structure

```
simple-web-app/
├── Dockerfile
├── index.html
└── README.md
```

* `Dockerfile` — Defines how the Nginx image is built
* `index.html` — Static web page served by Nginx
* `README.md` — Deployment documentation (this file)

---

## 🛠️ Prerequisites

Before starting, ensure you have:

* Docker installed
* Docker Desktop running (if on Windows or macOS)

Verify installation:

```bash
docker --version
```

---

## 🔧 Step 1: Review the Application Files

Before deploying, review the following files in this directory:

* **Dockerfile**
  Defines the base image, copies the web content, and exposes the required port.

* **index.html**
  Contains the static content served by Nginx.

Understanding these files is key to understanding how the container is built and deployed.

---

## 🔨 Step 2: Build the Docker Image

From the project directory, run:

```bash
docker build -t simple-nginx-web .
```

This command builds the Docker image using the instructions defined in the `Dockerfile`.

---

## ▶️ Step 3: Run the Docker Container

Start the container using:

```bash
docker run -d -p 8080:80 --name simple-web-app simple-nginx-web
```

This:

* Runs the container in detached mode
* Maps port 8080 on your machine to port 80 in the container
* Starts the Nginx web server

---

## 🌐 Step 4: Access the Web Application

Open your browser and navigate to:

```
http://localhost:8080
```

You should see the static web page served from `index.html`.
<img width="1214" height="768" alt="Ubuntu-2026-01-08-02-53-55" src="https://github.com/user-attachments/assets/4cbc722a-c933-414f-b7f8-279419f9bd32" />


---

## 🛑 Step 5: Stop and Clean Up

Stop the container:

```bash
docker stop simple-web-app
```

Remove the container:

```bash
docker rm simple-web-app
```

---

## 🧪 Docker Concepts Demonstrated

* Writing and using a Dockerfile
* Building Docker images
* Running containers
* Port mapping
* Using official base images (Nginx)
* Serving static content inside a container

---

## 📈 Why This Project Is Useful

This project reflects a **real-world container deployment pattern** commonly used to:

* Serve static websites
* Test frontend builds
* Learn container fundamentals

---

## ✅ Result

By completing this project, you have:

* Built a custom Docker image
* Deployed a containerized web application
* Served content using Nginx

🚢 **Simple. Clean. Production-aligned.**
