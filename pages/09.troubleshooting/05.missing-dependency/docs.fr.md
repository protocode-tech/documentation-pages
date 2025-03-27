---
title: 'Dépendance manquante dans l''environnement'
---

Lors du démarrage d'un environnement, une erreur de type `<binary> not found` est retournée. Cela signifie que vous essayer d'exécuter un binaire qui n'est pas installé sur l'environnement. 

## Appel à un binaire non installé

Pour rappel, l'environnement sur Protocode est une machine Debian 11 qui n'embarque qu'une certain nombre d'[outils nécessaires à son fonctionnement](/connecter-ses-outils/environment-anatomy#outils-preinstalles). Vous pouvez tout à fait en ajouter, notamment en appelant apt ou apt-get, et cela dans le cadre du [cycle de vie d'un environnement](/configurer-son-projet/scripts-dinitialisation#evenements-du-cycle-de-vi) pour que ce soit fait automatiquement au démarrage d'un environnement.

## Problème de positionnement

Il arrive aussi que l'on oublie que depuis un terminal, on se trouve dans l'environnement (machine hôte) et non dans le conteneur de l'application, et inversement.

Prenons l'exemple d'un projet javascript. Appeler `npm install` depuis un nouveau terminal ouvert devrait déboucher sur une erreur "_npm not found_". Pour lancer npm il faudrait lancer une commande docker-compose du type `docker-compose run --rm app npm install` puisque npm ne tourne pas dans l'environnement, mais dans un conteneur.

Inversement, si je me positionne dans un conteneur avec une commande de type `docker-compose exec app bash`, puis que j'appelle git, il est probable qu'une erreur "git not found" soit retournée, puisque git n'est pas installé dans mon conteneur, mais dans l'environnement. La solution est alors soit de lancer une commande `exit` pour retourner dans le terminal de l'environnement, soit d'en ouvrir un nouveau.