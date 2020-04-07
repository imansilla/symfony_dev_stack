# Symfony Docker Development Stack

This is a stack based on lightweight Linux Distributions for running the latest version of **Symfony Framework** into Docker containers using **docker-compose**

It was designed to be used with **Symfony**, but it can be used with any other PHP Framework

### Prerequisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Containers

- nginx (proxy)
- php-fpm
- php-cli (composer)
- nginx (server)
- mysql (database)
- phpmyadmin (GUI for mysql)

## Steps to Use

1. Create the `.docker/.env` file, copying it from `.docker/.env.example`
2. Replace the default environment variables values on `.docker/.env` file
3. Replace `${PROJECT_NAME}` for the real value of the project name on `.docker/nginx/vhost.conf`
4. Add entries to `/etc/hosts` (host machine) file for the locals domains specified in `VIRTUAL_HOST` variables inside `docker-compose.yml` 
    - `127.0.0.1 admin.${PROJECT_NAME}.local phpmyadmin.${PROJECT_NAME}.local` (replace `${PROJECT_NAME}` with the real value)
5. Run `docker-compose up -d` 

## Install Symfony Framework

1. Move to the `.docker` directory, where the `docker-compose.yml` file is located
2. Run once `$ docker-compose run --rm php-cli composer create-project symfony/website-skeleton symfony`
3. Run once `$ mv symfony/{.[!.],}* . ; rm -rf symfony`
4. You can visit: 
  - `http://admin.${PROJECT_NAME}.local` 
  - `http://phpmyadmin.${PROJECT_NAME}.local`

## Additional

If you wanna to install other dependencies with **composer**, run the following

1. Move to the `.docker` directory, where the `docker-compose.yml` file is located
2. Install any needed dependencies, example **Sonata Admin Bundle**
  - `docker-compose run --rm php-cli composer require sonata-project/admin-bundle`
  - `docker-compose run --rm php-cli composer require sonata-project/doctrine-orm-admin-bundle`

## Note

After cloning the project you can modify it according to your need