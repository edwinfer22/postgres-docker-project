# PostgreSQL Docker Project

This project sets up a PostgreSQL database and pgAdmin 4 using Docker Compose.

## Prerequisites

- Docker
- Docker Compose

## How to Run

1.  Navigate to the project directory:
    ```sh
    cd postgres-docker-project
    ```
2.  Start the PostgreSQL database and pgAdmin service:
    ```sh
    docker-compose up -d
    ```

## Connecting to PostgreSQL

### Via psql (Command Line)

You can access the PostgreSQL command-line client (`psql`) inside the running container:

```sh
docker exec -it postgres-docker-project-db-1 psql -U user mydatabase
```
*   Basic psql commands: `\l` (list databases), `\dt` (list tables), `\q` (exit).

### Via pgAdmin 4 (Web Interface)

1.  Open your web browser and go to: `http://localhost:5050`
2.  **Log in:**
    *   **Email:** `admin@example.com`
    *   **Password:** `admin`
3.  **Register a new server in pgAdmin:**
    *   Right-click "Servers" in the left panel -> "Register" -> "Server...".
    *   **General Tab:** Name it (e.g., `My PostgreSQL`).
    *   **Connection Tab:**
        *   **Host name/address:** `db` (This is the service name within the Docker network)
        *   **Port:** `5432`
        *   **Maintenance database:** `mydatabase`
        *   **Username:** `user`
        *   **Password:** `password`
    *   Click "Save".

## Stopping the Services

To stop and remove the containers (your data will be preserved in the `postgres_data` volume):

```sh
docker-compose down
```

## Cleaning Up Data (Optional)

If you want to completely remove the database data (volume), use:

```sh
docker-compose down -v
```
