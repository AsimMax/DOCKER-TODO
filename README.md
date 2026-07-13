# DOCKER-TODO
# MERN Todo App with Docker Compose

A simple full-stack Todo application built with **MongoDB, Express, React, and Node.js (MERN)**, fully containerized using Docker. This project was built as a hands-on learning exercise to understand Docker fundamentals — including multi-container orchestration, container networking, environment variable management, and persistent data storage with volumes.

## 🛠️ Tech Stack

- **Frontend:** React (Vite)
- **Backend:** Node.js, Express
- **Database:** MongoDB
- **Database GUI:** Mongo Express
- **Containerization:** Docker, Docker Compose

## 📦 Architecture

The app runs as four separate services, each in its own container, connected over a shared Docker network:

| Service        | Description                          | Port   |
|----------------|---------------------------------------|--------|
| `frontend`     | React (Vite) client                   | 5173   |
| `backend`      | Express REST API                      | 5000   |
| `mongo`        | MongoDB database                      | 27017  |
| `mongo-express`| Web-based MongoDB admin UI            | 8081   |

## ✨ Features

- Add, toggle, and delete todos
- RESTful API (`GET`, `POST`, `PATCH`, `DELETE`) backed by MongoDB
- Persistent data storage via Docker volumes (data survives container restarts)
- Isolated container networking — services communicate using Docker service names, not `localhost`
- Environment-based configuration using `.env` files

## 🚀 Getting Started

### Prerequisites
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running

### Setup

1. Clone the repository
   ```bash
   git clone <your-repo-url>
   cd mern-todo
   ```

2. Create `.env` files based on the provided `.env.example` files in `backend/` and the project root.

3. Build and start all services:
   ```bash
   docker compose up --build
   ```

4. Open the app:
   - Frontend: [http://localhost:5173](http://localhost:5173)
   - Backend health check: [http://localhost:5000/health](http://localhost:5000/health)
   - Mongo Express (DB admin UI): [http://localhost:8081](http://localhost:8081)

### Stopping the app

```bash
docker compose down
```

To also remove the database volume (⚠️ deletes all data):

```bash
docker compose down -v
```

## 📁 Project Structure

```
mern-todo/
├── backend/
│   ├── models/
│   ├── routes/
│   ├── server.js
│   ├── Dockerfile
│   └── package.json
├── frontend/
│   ├── src/
│   ├── index.html
│   ├── Dockerfile
│   └── package.json
├── compose.yaml
└── README.md
```

## 📚 What I Learned

This project was built to practice:
- Writing Dockerfiles for a Node.js backend and a Vite-based React frontend
- Orchestrating multi-container apps with `docker-compose.yaml`
- Container-to-container networking (using service names instead of `localhost`)
- Managing secrets and config via environment variables and `.env` files
- Using named volumes for persistent MongoDB storage
- Debugging containerized apps using `docker compose logs` and Docker Desktop

## 📝 License

This project is open source and available for learning purposes.
