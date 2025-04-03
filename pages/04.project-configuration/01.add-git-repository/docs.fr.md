---
title: 'Ajout d''un dépôt GIT'
taxonomy:
    category:
        - docs
slug: ajout-depot-git
---

Dans Protocode, nous distinguons les projets et les dépôts GIT, bien qu'il arrive souvent que ces notions se rejoignent. Le projet est une notion globale, qui englobe une ou plusieurs sources, mais aussi les tâches à faire et les membres de l'équipe.  

Lorsqu'un projet est créé, la deuxième étape est d'ajouter les dépôts. Pour les projets monobloc, il n'y en aura qu'un. Mais dans des projets complexes, il pourra y en avoir plusieurs. Par exemple, un dépôt avec une API, et un autre avec un site en JavaScript qui consomme l'API.

[plugin:youtube](https://www.youtube.com/watch?v=TUF88b-nwTM)

L'ajout d'un dépôt se fera en 3 étapes :  

* **L'identification** : le remplissage de l'URL de celui-ci. L'URL peut être celle d'un dépôt hébergé sur GitHub, mais aussi GitLab (public ou privé), ou encore BitBucket.  

* **L'attribution des droits en lecture et écriture à Protocode**. Protocode va générer une clé SSH qu'il faudra reporter en tant que clé de déploiement **avec les droits en écriture**.  

* **Le choix de la branche par défaut** : celle sur laquelle sera positionné l'utilisateur à l'ouverture d'un environnement.  

Une fois ces étapes remplies, Protocode est capable de récupérer et pousser des modifications vers le code source, mais il n'est pas encore en mesure de l'exécuter. Cette partie relève de l'étape suivante : la virtualisation.
