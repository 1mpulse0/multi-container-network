
# Multi-Container Network

## Description

This project demonstrates a multi-container application using Docker. It consists of three services: a frontend, a backend, and a database.

The frontend displays user information and retrieves data from the backend through a REST API. The backend is developed using Python Flask and connects to a PostgreSQL database to retrieve user records.

All services communicate through a shared Docker bridge network.

## Technologies Used

- Python
- Flask
- Nginx
- PostgreSQL
- Docker
- Docker Compose
- REST API

## Project Structure

```text
multi-container-network/
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
├── frontend/
│   ├── index.html
│   ├── nginx.conf
│   └── Dockerfile
├── docker-compose.yml
├── .gitignore
└── README.md
```

## Application Architecture

The application contains three main services:

- **Frontend:** An Nginx web server that displays the user dashboard and sends API requests.
- **Backend:** A Python Flask application that provides a REST API and retrieves user data from the database.
- **Database:** A PostgreSQL database that stores user information.

The frontend communicates with the backend through the `/api/users` endpoint. The backend connects to PostgreSQL using the Docker service name `db`.

## Network Configuration

All three services are connected to a shared Docker bridge network named `app-network`.

The frontend is accessible through port `8080`, while the backend and database use internal container ports.

## Database Storage

PostgreSQL data is stored in a named Docker volume called `postgres_data`. This allows database records to persist when containers are stopped or recreated.

## API Endpoint

**GET /api/users**

Returns a JSON list of users stored in the PostgreSQL database.

Example response:

```json
[
  {
    "id": 1,
    "name": "John Smith",
    "email": "john@example.com"
  },
  {
    "id": 2,
    "name": "Anna Brown",
    "email": "anna@example.com"
  },
  {
    "id": 3,
    "name": "Michael Green",
    "email": "michael@example.com"
  }
]
```

## Requirements

- Three services defined in `docker-compose.yml`.
- Separate Dockerfiles for the frontend and backend.
- Frontend communication with the backend through a REST API.
- Backend connection to PostgreSQL using the database service name.
- Docker bridge network for communication between containers.
- Port mapping for external access to the frontend.
- Persistent database storage using a Docker volume.

## Conclusion

This project demonstrates how a frontend, backend, and database can work together in a Docker environment. It illustrates container networking, REST API communication, database connectivity, and persistent data storage using Docker Compose.
