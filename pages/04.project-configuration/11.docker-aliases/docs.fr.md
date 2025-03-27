---
title: 'Alias docker'
taxonomy:
    category:
        - docs
slug: alias-docker
media_order: 'alias_up_FR.png,alias_portee_FR.png'
---

`FONCTIONNALITÉ EN BÊTA`

La proposition est d'abstraire Docker dans le terminal lorsque l'on se trouve à la racine d'un dépôt. Pour ce faire, Protocode vous propose de créer de manière automatisée des alias de terminal qui permettent d'appeler des exécutables à l'intérieur des conteneurs comme s'ils étaient dans la machine hôte.

Prenons un exemple. Imaginons qu'un dépôt utilise une image disposant de NodeJS. Pour l'appeler, vous devriez faire une commande du type :

[prism classes="language-bash"]
$ docker-compose run --rm app node --version
v16.0.0
[/prism]

Avec les alias, on peut simplement écrire :

[prism classes="language-bash"]
$ node --version
v16.0.0
[/prism]

## Déclaration des alias

La déclaration des alias se fait directement dans le fichier docker-compose, au niveau d'un conteneur, dans la clé "labels".
`protocode.alias.{{ nom_de_mon_executable }}`: `commande docker compose équivalente`.

[prism classes="language-yaml line-numbers" highlight="8,9"]
# Fichier docker-compose.yml du dépôt
version: '3.8'
services:
  app:
    image: "node:16"
    ...
    labels:
      protocode.alias.node: docker-compose run --rm app node
      protocode.alias.npm: docker-compose run --rm app npm
[/prism]

Ce qui aura pour effet, au démarrage des conteneurs, d'installer les alias :

![alias_up_FR](alias_up_FR.png?style=max-width:35rem;)

## Portée des alias

Les alias ainsi créés n'ont d'effet qu'à la racine du dépôt dans lequel se trouve le fichier docker-compose qui les a créés.

Voici donc ce qui se produit si on se déplace sur le répertoire parent :

![alias_portee_FR](alias_portee_FR.png?style=max-width:25rem;)

## Génération automatique

Dans les projets configurés automatiquement par IA, ainsi que les projets qui utilisent les images préconfigurées de Protocode, les alias pertinents sont automatiquement ajoutés. Pour les projets Laravel ou Symfony, au-delà de php, il est même possible d'appeler directement artisan ou bin/console.
