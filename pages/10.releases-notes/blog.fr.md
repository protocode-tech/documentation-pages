---
title: 'Notes de mises à jour'
slug: notes-mises-a-jour
---

## 21/03/2025: Mises à jour des environnements
* Mise à jour de Docker, Docker Compose, DinD, PHP, vendors, Git, Visual Studio Code, Codeserver.
* Ajout du plugin Docker Compose permettant désormais d'appeler `docker compose <command>`.

## 19/03/2025: Améliorations et correctifs
* `VIRTUAL_HOST` n'est plus obligatoire pour exposer un conteneur, l’attribution de port via "XXXX:XXXX" fonctionne aussi.
* Amélioration du processus de remise en marche : les ressources allouées et délais avant mise en sommeil sont désormais mis à jour.
* Correctif fixant une erreur à la remise en marche d'un environnement dont le compte utilisateur de l'agent a été supprimé.

## 15/03/2025: Fonctionnalité - Devcontainer
* Ajout de la fonctionnalité de paramétrer son dépôt à partir d'un fichier `devcontainer.json` existant.

## 11/03/2025: Amélioration - Lancement automatique de processus
* Lancement automatique des processus de préconstruction Docker et de mise en cache lorsqu'obligatoires.

## 02/02/2025: Correctif
* Correction d'un problème de droits affectant l'image préconfigurée Prestashop.

## 15/01/2025: Fonctionnalité - Synchronisation des préférences utilisateurs
* Création d'un plugin VSCode permettant de synchroniser les thèmes, raccourcis et préférences de l'instance locale avec Protocode. Il permet aussi de synchroniser les alias du terminal (bash, zsh) pour les utilisateurs Mac et Unix.

## 06/12/2024: Fonctionnalité & correctif - Autoconfiguration par IA
* Intégration d'un nouveau module configurant automatiquement les dépôts grâce à une IA.
* Correction d'une erreur de `docker-compose` au lancement d'un environnement lorsque le réseau Docker n'est pas encore lancé.

## 13/12/2024: Amélioration - Nouvelle image préconfigurée
* Ajout de PHP 5.6 dans les images préconfigurées pour le support de projets "Legacy".

## 05/07/2024: Style - Refonte des interfaces de l'application
* Interface complètement repensée pour fluidifier la navigation entre les Workspaces et les tâches, et simplification des écrans de configuration de dépôt.

## 06/12/2024: Amélioration - Nouvelles images préconfigurées
* Ajout des images MongoDB, PostgreSQL, Mongo Express, Python, Go et Java en tant qu'images préconfigurées dans la configuration d'un dépôt.

## 31/10/2024: Amélioration - Nouvelles stacks dans le module de démo
* Ajout des stacks Angular, Symfony, Laravel et Drupal au lancement du module de démonstration.

## 30/10/2024: Amélioration - Page non trouvée sur les environnements
* Une nouvelle "page non trouvée" a été créée pour les environnements, afin que l'utilisateur comprenne plus facilement l'origine de l'erreur et trouve les solutions les plus courantes.

## 17/10/2023: Fonctionnalité - Magic links
* Nouvelle fonctionnalité permettant d'avoir une URL qui réouvre l'environnement s'il était en pause.

## 13/09/2023: Fonctionnalité - Module de démo
* Ajout d'un module de démonstration permettant de tester la solution en conditions réelles depuis la page d'accueil du site.

## 22/08/2023: Correctif
* Correction d'un bug affectant le calcul du nombre d'environnements ouverts dans un espace en cas d'erreur à l'ouverture d'un environnement.

## 30/06/2023: Amélioration - Internationalisation
* Refonte de la page d'accueil.
* Internationalisation complète de l'application pour les langues anglaise et française.

## 13/06/2023: Amélioration - Remise en marche des environnements
* Les erreurs pouvant survenir pendant la remise en marche d'un environnement en pause ne sont plus bloquantes pour sa réouverture.

## 08/06/2023: Correctifs
* Correction d'un problème affectant les utilisateurs de l'interface web de VSCode, dont les environnements se trouvaient mis en pause de manière intempestive. 
* Correction d'un problème affectant les environnements mis en pause après l'ajout d'un nouveau dépôt dans la configuration du projet.

## 05/06/2023: Amélioration - Mise en pause / remise en marche
* Modification de l'architecture utilisée pour la mise en pause, permettant de diviser par 5 le temps de mise en pause, et par 4 celui de la remise en marche.

## 22/05/2023: Améliorations - Modifications des volumes des images préconfigurées
* L'interface de paramétrage de la virtualisation permet désormais de modifier/ajouter/supprimer des volumes au sein du mode "Utiliser les images préconfigurées de Protocode".

## 05/05/2023: Améliorations - Utilisateur rootless et images préconfigurées
* L'utilisateur rootless `protocode` a désormais l'ID 1000, afin de simplifier la gestion des droits avec de nombreuses images Docker partageant cet ID.
* Toutes les images préconfigurées ont désormais l'ID 1000 pour l'utilisateur du processus principal (`www-data` pour PHP, par exemple).
* Les images de Prestashop et de WordPress ont été améliorées pour s'intégrer nativement dans l'écosystème Protocode (versions "plug-n-play").
* Les images Node 20, PHP 8.2, Adminer et MailDev ont été ajoutées dans les images préconfigurées.
* Correction d'un bug empêchant la préconstruction d'images dans les dépôts où la version de `docker-compose` utilisée était la V1.

## 21/04/2023: Correctifs - Lien de prévisualisation sur les environnements mis en pause
* Correction liée à l'ajout de la dissociation des environnements vis-à-vis des configurations de dépôts. Les liens de prévisualisation n'étaient plus affichés sur l'interface web pour les environnements remis en marche.

## 20/04/2023: Amélioration - Remise en marche des environnements
* La remise en marche des environnements est désormais dissociée des configurations de dépôts. Cela évite que les modifications de configuration créent des erreurs bloquant la remise en marche des environnements mis en pause.

## 04/04/2023: Correctif
* Correction d'un bug lié à l'ajout des environnements rootless. Les extensions VSCode n'étaient plus installées avec la commande `code --install-extension`.

## 01/04/2023: Modification du plan tarifaire
* Retrait des plans Pay As You Go Individuals et Pay As You Go Entreprise, ainsi que du plan Developer.
* Modification du plan Starter, devenu gratuit, offrant 50 crédits mensuels, sans dépassement possible.
* Ajout du pack Pro, à 9€ par mois, offrant 100 crédits mensuels, avec dépassement facturé à 0.18€/crédit.

## 23/03/2023: Fonctionnalité - Ajout d'un nouveau hook de cycle de vie
* Ajout d'un nouveau hook permettant d'ajouter du traitement avant la mise en veille d'un environnement.

## 16/02/2023: Correctifs & Améliorations
* Correction de l'erreur "Git Unsafe Repository".
* Amélioration du processus de build. Identification exacte des images à construire et construction de ces images seules. Plus de `pull` des autres images du fichier `docker-compose`. Le processus de préconstruction n'est plus obligatoire si toutes les images sont déjà préconstruites.

## 10/02/2023: Correctifs & changements mineurs
* Correction de l'erreur retournée à la mise en pause des environnements lors de la compression de fichiers volumineux modifiés en cours de processus.
* La version par défaut de `docker-compose` passe de la v1 à la v2.
* Ajout des liens vers le changelog et le statut des services.
