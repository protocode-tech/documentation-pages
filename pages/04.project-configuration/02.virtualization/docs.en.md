---
title: Virtualization
visible: true
taxonomy:
    category:
        - docs
media_order: 'docker_vars_FR.png,docker_vars_EN.png'
---

In Protocode, once a repository has been added, the next step is to manage the "virtualization." In other words, manage the dependencies necessary for its execution. For example, the need to have PHP installed, or even MySQL or NodeJS.

To achieve this, Protocode relies on [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/), the multi-container manager. This allows Protocode to run even in complex projects, particularly those with microservices.

## Choosing a Virtualization Strategy

You will need to establish a Docker Compose configuration for each repository. To help with this, Protocode’s configuration tool gives you the option to choose from 4 strategies:

* **Write a docker-compose file inline**: This option allows you to manually input the content of a Docker Compose file. It will be used to start the environment but is not versioned with the project. This is the most suitable solution if your project has no specific complexities and you can rely on pre-built images (especially those from [Docker Hub](https://hub.docker.com/)).

* **Use a docker-compose file within your Git repository**: This solution is the best option if you already have an existing configuration or if you want to create one (which is usually necessary when the repository’s requirements cannot be met by Docker's standard images).

* **Use pre-built Protocode images**: This allows you to create a Docker Compose configuration without writing any code, by selecting primary services (PHP, Node, etc.) and secondary services (database, mailer, etc.). This is the best solution if you are not yet comfortable with Docker.

* **Use a devcontainer.json file** `IN BETA`: This allows you to use an existing devcontainer configuration file in your repository. It will be used to generate a Docker and Docker Compose configuration, as well as a set of scripts run when the environment starts.

## Editing the Docker Compose File for Protocode

Editing a Docker Compose file for Protocode is the same as editing one for local use. You can rely on the configuration as described in the [official Docker Compose documentation](https://docs.docker.com/compose/).

If you are not familiar with Docker or Docker Compose, don’t worry, [let the AI handle it](/project-configuration/ai-assisted-configuration).

## Docker Compose Environment Variables

Your Docker Compose configuration can rely on variables injected into the containers, such as environment variables. It is quite common to see something like this:


[prism classes="language-yaml line-numbers" highlight="7,8,9,10,11,15,16,17,18,19,20"]
version: "3"
services:
    database:
        image: "mysql:8.0"
        command: --default-authentication-plugin=mysql_native_password
        environment:
            - "MYSQL_DATABASE=${DB_NAME}"
            - "MYSQL_USER=${DB_USER}"
            - "MYSQL_PASSWORD=${DB_PASSWORD}"
            - "MYSQL_ROOT_PASSWORD=${DB_PASSWORD}"
            - "MYSQL_PORT=${DB_PORT}"
    phpmyadmin:
        image: phpmyadmin/phpmyadmin
        environment:
            - "VIRTUAL_HOST=phpmyadmin.${ENVIRONMENT_URL}"
            - "MYSQL_USERNAME=${DB_USER}"
            - "MYSQL_PASSWORD=${DB_PASSWORD}"
            - "PMA_USERNAME=${DB_USER}"
            - "PMA_PASSWORD=${DB_PASSWORD}"
            - "PMA_HOSTS=database"
        links:
            - database
[/prism]

In this example, there are two containers. The first is a MySQL database, and the second runs PhpMyAdmin. Both containers need certain variables, such as the username or password for the database. Rather than repeating the values of these variables in each container, we refer to shared variables here. It would be possible to create an .env file containing these variables. However, Protocode allows you to input these variables in its interface in a key/value table:

![docker_vars_EN](docker_vars_EN.png?style=max-width:35rem;)

These values will be provided to Docker Compose during container build and exist only within Protocode. They are not versioned in your repository.