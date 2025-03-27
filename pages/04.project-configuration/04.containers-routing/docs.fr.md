---
title: 'Routing vers les conteneurs'
taxonomy:
    category:
        - docs
slug: routing-conteneurs
---

Le "routing" est la capacité d'exposer un conteneur sur une URL accessible publiquement. Cela se configure dans le fichier docker-compose.yml, au niveau de chaque conteneur. Protocode propose deux méthodes pour gérer cette exposition :

## Présence d'une variable VIRTUAL_HOST

Si un conteneur dispose d'une variable `VIRTUAL_HOST`, Protocode génèrera automatiquement une URL de prévisualisation:

[prism classes="language-yaml line-numbers" highlight="6,7"]
version: "3"
services:
    app:
        image: "node:16"
        environment:
            VIRTUAL_HOST: "app-my-repository.${ENVIRONMENT_URL}"
[/prism]

!!! Peu importe la valeur saisie dans la variable VIRTUAL_HOST, **elle sera remplacée lors de la construction de l'environnement** en fonction de l'url du serveur qui l'hébergera.

## Allocation de ports

Si un conteneur spécifie une allocation de port sur la machine hôte, Protocode générera également une URL de prévisualisation :

[prism classes="language-yaml line-numbers" highlight="6"]
version: "3"
services:
    app:
        image: "node:16"
        ports:
        	- "8080:8080"
[/prism]

!!! Une particularité est à noter. Bien que votre configuration alloue un port de la machine hôte à votre conteneur, l'url qui sera générée par Protocode sera toujours sur le port 443. L'environnement redirigera ensuite cet appel en interne vers le port attendu par le conteneur.

## Urls des conteneurs

Protocode construit les URLs des conteneurs selon la convention suivante :

`NOM_DU_SERVICE`-`SLUG_DU_REPOSITORY`.`URL_DE_L_ENVIRONNEMENT`

Les deux premières parties sont déductibles facilement :
* **NOM_DU_SERVICE**: c'est le nom du conteneur dans le fichier docker-compose. Dans l'exemple précédent, c'est "app".
* **SLUG_DU_REPOSITORY**: provient du nom du dépôt Git, en supprimant l'extension .git.
Exemple : pour `githost.ext/me/my-repository.git`, le slug sera `my-repository`.

La dernière partie, URL_DE_L_ENVIRONNEMENT, est déterminée dynamiquement par Protocode et peut varier en fonction de plusieurs paramètres (namespace de l’environnement, serveur, etc.). Elle est néanmoins accessible dans chaque environnement via la variable d’environnement `ENVIRONMENT_URL`.

## Communication entre les services

Si un service doit communiquer avec un autre (par exemple, un frontend et une API), il peut utiliser ENVIRONMENT_URL pour construire dynamiquement les URLs :

[prism classes="language-yaml line-numbers" highlight="9,15"]
# Dans le fichier docker-compose d'un repository githost.ext/me/my-repository.git
version: "3"

services:
    api:
        image: "php:8.0"
        environment:
            VIRTUAL_HOST: "api-my-repository.${ENVIRONMENT_URL}" # L'API doit être exposée
            FRONT_URL: "front-my-repository.${ENVIRONMENT_URL}" # Elle a besoin de l'URL du frontend

    front:
        image: "node:16"
        environment:
            VIRTUAL_HOST: "front-my-repository.${ENVIRONMENT_URL}" # Le frontend doit être exposé
            API_URL: "api-my-repository.${ENVIRONMENT_URL}" # Il a besoin de l'URL de l'API
[/prism]
