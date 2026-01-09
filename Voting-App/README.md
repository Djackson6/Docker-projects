# 🚀 Voting App Deployment with Docker Compose

This project demonstrates deploying an example voting application with Docker Compose. The Compose file (compose.yaml) starts a vote frontend, a result frontend, a worker, Redis, and a Postgres database.


## Services overview

- vote-app
  - Image: `vote`
  - Exposed on host port `8080` → container port `80`
  - Frontend to submit votes
- result-app
  - Image: `result`
  - Exposed on host port `8081` → container port `80`
  - Shows voting results
- worker-app
  - Image: `worker`
  - Background worker that consumes votes, updates DB, reads from Redis, etc.
- redis
  - Image: `redis:alpine`
  - In-memory queue/cache used by the worker and apps
- db
  - Image: `postgres:alpine`
  - Uses `.env` (env_file) to load `POSTGRES_USER` and `POSTGRES_PASSWORD`


## .env file

Create a `.env` file in `Voting-App/` (same directory as `compose.yaml`) with at least:

```
POSTGRES_USER=voting_user
POSTGRES_PASSWORD=change_this_password
```

The Compose file uses `env_file: - .env` and injects those variables into the `db` service.

## Build the images 

The folders contains Dockerfiles for each component (e.g., `vote/`, `result/`, `worker/`) build them from the appropriate directory:

```bash
# from repo root (adjust paths if Dockerfiles are elsewhere)
docker build -t vote ./Voting-App/vote
docker build -t result ./Voting-App/result
docker build -t worker ./Voting-App/worker
```

## ▶️ Start the app

From the `Voting-App/` directory:

```bash
cd Voting-App
docker compose up -d
```

Docker Compose will create and start all services defined in the file.

## 🛑 Stop and remove

```bash
# Stop
docker compose down

# Stop and remove images created by compose
docker compose down --rmi local --volumes --remove-orphans
```

## 🌐 Accessing the apps

- Vote UI: http://localhost:8080
- Result UI: http://localhost:8081
<img width="1211" height="800" alt="Ubuntu-2026-01-09-14-30-33" src="https://github.com/user-attachments/assets/fc2ec3e8-785e-403d-98b2-a877cda06527" />
<img width="1213" height="800" alt="Ubuntu-2026-01-09-14-30-42" src="https://github.com/user-attachments/assets/a6e5f07c-d00d-46b1-9bab-16efe91d6de5" />

## 🧪 Docker Concepts Demonstrated

* Writing and using a docker compose file
* Building Docker images
* Running containers
* Port mapping
* Using official base images (Redis/Postgres)
* Serving an app inside a container

---

## 📈 Why This Project Is Useful

This project reflects a **real-world container deployment pattern** commonly used to:

* Serve websites
* Test frontend and backend builds

---

## ✅ Result

By completing this project, you have:

* Deployed a containerized web application using docker compose 
