# DOCKER

This repository contains Docker images and Docker Compose files for creating development environments.

## How to install an image

To build a Docker image and run a container to work with your project, follow the instructions below:

1. Enter the [repository URL](https://github.com/juanmacivico87/docker). Surely, if you are reading this, you are already there.
2. Open a terminal and run the command ```git clone https://github.com/juanmacivico87/docker.git```.
3. Follow the instructions of the image you want to build for your project.

## Available images

| Image | Description |
|---|---|
| [LAMP](./lamp) | Docker image for creating a LAMP development environment |

## How to run Docker Compose files

To run a Docker Compose file and started containers to work with your project, follow the instructions below:

1. Repeat steps 1 and 2 of section **How to install an image**
2. Create an ```.env``` file and add the environment variables. In the example I put all the ones that are available in all Docker Compose files, but use only the ones you need:

```
# Database connection

MYSQL_DATABASE=my_awesome_database_name
MYSQL_USER=my_awesome_database_user
MYSQL_PASSWORD=my_awesome_database_password
MYSQL_ROOT_PASSWORD=my_awesome_database_root_password
```

3. Enter Docker Compose file you want to run and edit the values you need (container names, ports, volumes,...)
4. Run ```docker-compose -f docker-compose-file-name.yml up -d``` command, replacing *docker-compose-file-name.yml* with the name of the Docker Compose file you want to run. For example, if the file you want to run is called *docker-php-mysql.yml*, the command you should run would be ```docker-compose -f docker-php-mysql.yml up -d```

## Available Docker Compose files

| File | Description |
|---|---|
| docker-php-mysql.yml | Create containers to run a project with PHP and MySQL |