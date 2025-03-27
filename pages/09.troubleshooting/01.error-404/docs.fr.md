---
title: 'Erreur 404 sur les environnements'
media_order: error_404.png
---

En vous rendant sur l'URL de prévisualisation d'un environnement, le serveur peut vous retourner une erreur 404 comme celle-ci :

![error_404](error_404.png?style=max-width:35rem;)

Cela signifie que l'environnement répond bien, mais qu'aucun conteneur n'est trouvé pour cette URL.

## Vérification du statut du conteneur

Le problème peut venir du fait que le conteneur rencontre une erreur au démarrage. Vous pouvez vérifier s'il est bien opérationnel avec la commande suivante :

[prism classes="language-bash"]
docker-compose ps <nom_du_service>
[/prism]

Exemple:
[prism classes="language-bash"]
$ docker-compose ps app
NAME     IMAGE     COMMAND                  SERVICE      CREATED        STATUS         PORTS
my_app   php-7.4   "/usr/local/bin/entr…"   app          5 mins ago     Up 5 mins      80/tcp
[/prism]

* **Si le statut est "Up"**, le conteneur est bien opérationnel.
* **Si le statut est "Restarting"** : il rencontre un problème au démarrage.

## Consultation des logs du conteneur

Si votre conteneur redémarre en boucle, vous pouvez consulter ses logs pour identifier l'erreur :

[prism classes="language-bash"]
$ docker-compose logs <nom_du_service> -f
[/prism]

Les logs de sortie vous donneront des indications précieuses sur l'origine du problème.

## Causes fréquentes du problème

1. **Dépendances manquantes**

Vérifiez que toutes les dépendances sont bien installées. Par exemple :
[prism classes="language-bash"]
$ composer install # Pour les projets PHP
$ npm install # Pour les projets JavaScript
[/prism]

2. **Processus nécessaire au lancement**

Certaines applications nécessitent une compilation avant d'être fonctionnelles. 
Par exemple :
[prism classes="language-bash"]
$ npm start # Pour les application JavaScript
$ php artisan serve # Pour les projets Laravel
[/prism]

3. **Problème de routing**

Assurez-vous que le routing vers le conteneur est bien configuré. Consultez les [règles concernant le routing](/configurer-son-projet/routing-conteneurs).

4. **Lien obsolète**

Il est possible que l'environnement ait été mis en pause et que le lien que vous consultez soit obsolète. Retournez sur la tâche correspondante et cliquez sur le lien de prévisualisation pour avoir un lien à jour.

## Besoin d'aide ?

Si le problème persiste, [contactez le support](/ressources-support/contact-support).