# Worpik MySQL Deployment with Docker

This repository contains the necessary files to deploy a MySQL database using Docker. This setup is intended for testing and interview purposes for "Worpik".

## Prerequisites

- Docker installed on your machine
- Docker Compose (optional, but recommended)

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/manzana2164/DB.git
```

### Dockerfile

The `Dockerfile` sets up a MySQL database.

```dockerfile
# Use the official MySQL image from the Docker Hub
FROM mysql:latest

# Set environment variables
ENV MYSQL_ROOT_PASSWORD=Worpik123$
ENV MYSQL_DATABASE=worpik_db
ENV MYSQL_USER=manzana
ENV MYSQL_PASSWORD=Xperia1631$

# Expose the default MySQL port
EXPOSE 3306
```

### Docker Compose

For easier management, you can use Docker Compose. Create a `docker-compose.yml` file:

```yaml
version: "3.8"

services:
  mysql:
    build: .
    image: mysql:latest
    container_name: workpik_mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: Worpik123$
      MYSQL_DATABASE: worpik_db
      MYSQL_USER: manzana
      MYSQL_PASSWORD: Xperia1631$
    ports:
      - "3306:3306"
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```

### Build and Run the Container

To build and run the Docker container, use the following commands:

```bash
# Build the Docker image
docker build -t worpik-mysql .

# Run the Docker container
docker run -d -p 3306:3306 --name worpik_mysql workpik-mysql
```

If you are using Docker Compose, simply run:

```bash
docker-compose up -d
```

### Accessing the Database

You can access the MySQL database using any MySQL client. Use the following credentials:

- Host: `localhost`
- Port: `3306`
- User: `manzana`
- Password: `Xperia1631$`
- Database: `worpik_db`

## Cleanup

To stop and remove the Docker container, use the following commands:

```bash
docker stop worpik_mysql
docker rm worpik_mysql
```

If you used Docker Compose, run:

```bash
docker-compose down
```

## License

This project is licensed under the MIT License.

## Contact

For any questions or inquiries, please contact to emilio@enterlab.tech
