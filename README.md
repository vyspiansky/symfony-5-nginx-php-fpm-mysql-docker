# Symfony 5 (NGINX, PHP-FPM and MySQL) with Docker

Source: https://dev.to/martinpham/symfony-5-development-with-docker-4hj8

GitLab Repository: https://gitlab.com/martinpham/symfony-5-docker

There are 3 containers:

* MySQL, with mounted volume for data persistent
* PHP-FPM, with mounted volume for application’s code
* NGINX, with mounted volumes for configurations, logs, and share mounted volume with PHP-FPM for application’s assets

## Sample environment variables

The `.env` file content:

```
DATABASE_NAME=symfony
DATABASE_USER=appuser
DATABASE_PASSWORD=apppassword
DATABASE_ROOT_PASSWORD=secret

APP_ENV=dev
APP_SECRET=24e17c47430bd2044a61c131c1cf6990
```

## Symfony installation

```bash
symfony new src
```

## Start up

```bash
docker-compose up
```

When all containers are ready, open http://localhost to see a Symfony 5 welcome screen.

## Keep in mind

To wait until the MySQL container is Online to run migration script, [wait-for-it](https://github.com/vishnubob/wait-for-it) has been used.