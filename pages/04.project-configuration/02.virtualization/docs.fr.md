---
title: Virtualisation
visible: true
taxonomy:
    category:
        - docs
slug: virtualisation
media_order: docker_vars_FR.png
---

Lorsqu'un dépôt a été ajouté, reste ensuite à gérer la "virtualisation". Autrement dit, gérer les dépendances nécessaires pour son exécution. Par exemple, la nécessité d'avoir Php installé, voire MySQL ou encore NodeJS.

Pour ce faire, Protocode se repose sur [Docker](https://www.docker.com/) et sur [Docker Compose](https://docs.docker.com/compose/), le gestionnaire de conteneurs multiples. Ce qui vous permet de faire tourner Protocode même sur des projets complexes, contenant notamment des micro-services.

[plugin:youtube](https://www.youtube.com/watch?v=BMEw2yD-0Mk)

## Choix d'une stratégie de virtualisation

Il faudra donc établir une configuration Docker Compose pour chacun des dépôts. Dans cette optique, l'outil de configuration de Protocode vous propose de choisir entre 4 stratégies :

* **Écrire un fichier docker-compose en ligne** : cette option vous permet de saisir le contenu d'un fichier Docker Compose. Celui-ci sera utilisé pour le démarrage de l'environnement, mais n'est pas versionné au projet. C'est la solution la plus adaptée si votre projet n'a pas de complexités particulières, et que vous pouvez vous reposer sur des images préconstruites (notamment celles de [Docker Hub](https://hub.docker.com/)).

* **Utiliser un fichier docker-compose au sein de votre dépôt Git** : c'est la solution la plus adaptée si vous avez déjà une configuration existante, ou si vous souhaitez en avoir une (ce qui est généralement nécessaire lorsque les besoins du dépôt ne peuvent être comblés par les images standards de Docker).

* **Utiliser des images préconstruites de Protocode** : cela vous permet de créer une configuration Docker Compose sans écrire une ligne, par un jeu de sélection de services principaux (PHP, Node, etc.) et secondaires (base de données, mailer, etc.). C'est la solution la plus adaptée si vous n'êtes pas encore à l'aise avec Docker.

* **Utiliser un fichier devcontainer.json** `EN BETA` : cela vous permet d'utiliser un fichier de configuration devcontainer déjà existant dans votre dépôt. Il sera utilisé pour générer une configuration Docker et Docker Compose, ainsi qu'un ensemble de scripts lancés au démarrage de l'environnement.

## L'édition du fichier docker-compose destiné à Protocode

L'édition d'un fichier Docker Compose destiné à Protocode est identique à celle d'une utilisation locale. Vous pouvez donc vous reposer sur la configuration telle que décrite dans la [documentation officielle de Docker Compose](https://docs.docker.com/compose/).

Si vous n'êtes pas à l'aise avec Docker ou Docker Compose, pas de panique, [laissez l'IA s'en charger](/configurer-son-projet/configuration-par-ia).

## Les variables d'environnement Docker Compose

Votre configuration Docker Compose peut s'appuyer sur des variables injectées dans les conteneurs, comme des variables d'environnement. Il est assez courant de voir ceci :

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

Dans cet exemple, il y a deux conteneurs. Le premier est une base de données MySQL, et le second fait tourner PhpMyAdmin. Les deux conteneurs ont besoin de certaines variables, notamment le nom de l'utilisateur ou encore le mot de passe de la base. Plutôt que de répéter les valeurs de ces variables dans chaque conteneur, on préfère ici faire référence à des variables partagées. Dans l'absolu, il serait possible de créer un fichier .env contenant ces variables. Protocode vous offre cependant la possibilité de saisir dans son interface ces variables dans un tableau clé/valeur :

![docker_vars_FR](docker_vars_FR.png?style=max-width:35rem;)

Ces valeurs seront données à Docker Compose lors de la construction des conteneurs et n'existent qu'au sein de Protocode, et ne sont pas versionnées dans votre dépôt.