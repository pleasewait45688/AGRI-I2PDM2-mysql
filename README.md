# I2PDM2-mysql

MySQL service for the I2PDM2 pest-recognition backend. This repo has no
application code — just the docker-compose service definition and config.
It stores a single table, `pest_records`, that `I2PDM2-fastapi-backend`
writes one row to for every pest-detection request it handles.

## Quick Start

1. Copy `.env.example` to `.env` and set your own passwords. `MYSQL_USER` /
   `MYSQL_PASSWORD` here must match the `DATABASE_URL` set in
   `I2PDM2-fastapi-backend/.env` — that's the account the backend connects
   with.
2. Create the docker network shared with the backend (once, if it doesn't
   already exist): `docker network create pest_app_network`
3. `docker compose up -d`

## Deployment

```bash
# Build
docker compose up -d --build
# Start (without build)
docker compose up -d
# Stop
docker compose down
```

## Useful commands

```bash
# log in to mysql (password is MYSQL_ROOT_PASSWORD from .env)
docker exec -it pest_db_v1 mysql -u root -p

# then, inside the mysql shell:
USE pest_db_v1;
SHOW TABLES;
SELECT * FROM pest_records ORDER BY id DESC LIMIT 5;
```
