# Docker Nginx PHP MySQL

This project provides a Dockerized setup for running a web application with Nginx as the web server, PHP as the backend processing engine, and MySQL as the database. It is ideal for local development environments, ensuring consistency across different setups.

## Prerequisites

- Docker
- Docker Compose

## Project Structure

```
/
├── docker-compose.yml
├── nginx/
│   ├── default.conf
│   └── www/
├── mysql/
│   └── data/
└── php/
    └── Dockerfile (optional for custom PHP configurations)
```

- **`docker-compose.yml`**: The main configuration file for Docker Compose that defines all services (Nginx, PHP, MySQL).
- **`nginx/default.conf`**: Configuration file for Nginx.
- **`nginx/www/`**: Directory for serving your web files (e.g., PHP files).
- **`mysql/data/`**: Directory for MySQL data persistence.
- **`php/Dockerfile`**: Optional custom Dockerfile for building the PHP container (if needed for additional PHP configurations).

## Getting Started

### Step 1: Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/yourusername/docker-nginx-php-mysql.git
cd docker-nginx-php-mysql
```

### Step 2: Build and Start the Containers

Run the following command to start up the containers:

```bash
docker-compose up --build
```

This will:
- Build the containers for PHP, Nginx, and MySQL.
- Start all services defined in `docker-compose.yml` (Nginx, PHP, and MySQL).
- Set up a MySQL database with the name `ruby` and a root password of `root`.

## Configuration

### Nginx Configuration

The Nginx configuration file is located at `nginx/default.conf`. You can modify it according to your needs. By default, it will serve files from the `nginx/www` directory.

### PHP Configuration

The PHP container is based on the `php:7.3-fpm` image. You can customize the `php/Dockerfile` if you need additional PHP extensions or custom settings. The `nginx/www` directory is mounted to the PHP container for easy access to your code.

### MySQL Configuration

The MySQL container uses the `mysql:5.7` image and is configured with a root password (`root`) and a default database (`ruby`). The database data is persisted in the `mysql/data` directory. You can change the database credentials and configuration by editing the `docker-compose.yml` file.

## Stopping the Containers

To stop the containers, run:

```bash
docker-compose down
```

This will stop and remove the containers, but the data in the MySQL database will persist (unless you choose to remove the volumes).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
