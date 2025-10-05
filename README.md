# 🐘 PostgreSQL Docker Setup

This repository contains a **Docker Compose configuration** for running a PostgreSQL database.
It is designed for local development and testing purposes.

---

## ⚙️ Features

- PostgreSQL latest version
- Persistent data using Docker volumes
- Automatic restart on container failure
- Configurable username, password, and database name

---

## 🐳 Docker Compose Configuration

The `docker-compose.yml` includes:

```yaml
services:
  postgres:
    restart: always
    image: postgres:latest
    container_name: postgres
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: 12345678
      POSTGRES_DB: main
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```


---

## 🚀 Quick Start

1. Clone the repository

git clone https://github.com/yourusername/postgres-docker.git
cd postgres-docker

2. Start PostgreSQL

docker compose up -d

This command will:
	•	Pull the latest PostgreSQL image
	•	Create and start the container
	•	Map PostgreSQL port 5432 to your host
	•	Persist data in a Docker volume called postgres_data

---

## 🔑 Default Credentials

Variable	Value
User	postgres
Password	12345678
Database	main
Port	5432

You can change these in the docker-compose.yml file under environment.

---

## 🧹 Stop and Remove Containers

To stop the running container:

docker compose down

This will stop the container but keep your database data in the postgres_data volume.

To remove containers and volumes:

docker compose down -v


---

## 📦 Access PostgreSQL

You can connect using any PostgreSQL client (pgAdmin, DBeaver, psql):

psql -h localhost -p 5432 -U postgres -d main

It will prompt you for the password: 12345678.

---

## ⚙️ Notes
	•	The database data is persisted in a Docker volume (postgres_data) so that it survives container restarts.
	•	The container automatically restarts on failure because of restart: always.
	•	For production use, consider using stronger passwords and secure network configurations.
