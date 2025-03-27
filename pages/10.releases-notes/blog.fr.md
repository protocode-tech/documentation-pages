---
title: 'Notes de mises à jour'
slug: notes-mises-a-jour
---

## 2/02/2025: Correctif
* Fix d'un problème de droit affectant l'image préconfigurée Prestashop.

## 15/01/2025: Fonctionnalité - Synchronisation des préférences utilisateurs
* Création d'un plugin VSCode permettant de synchroniser les thèmes, raccourcis, et préférences de l'instance locale avec Protocode. Il permet aussi de synchroniser les alias du terminal (bash, zsh) pour les utilisateur Mac et Unix.

## 6/12/2024: Fonctionnalité & correctif - Autoconfiguration par IA
* Intégration d'un nouveau module configurant automatiquement les dépôts grace à un IA.
* Fix d'une erreur de docker-compose au lancement d'un environnement lorsque le réseau docker n'est pas encore lancé.

## 13/12/2024: Amélioration - Nouvelle image préconfigurée
* Ajout de php 5.6 dans les images préconfigurées pour le support de projet "Legacy".

## 05/07/2024: Style - Refonte des interfaces de l'application
* Interface complètement repensée pour fluidifier la navigation entre les Workspaces et les tâches, et qui simplifie les écrans de configuration de dépôt.

## 06/12/2024: Amélioration - Nouvelles images préconfigurées
* Ajout des images MongoDB, PostgresSQL, Mongo Express, Python, Go, Java en tant qu'images préconfigurées dans la configuration d'un dépôt.

## 31/10/2024: Amélioration - Nouvelles stack dans le module de démo
* Ajout des stack Angular, Symfony, Laravel et Drupal au lancement du module de démonstration.

## 30/10/2024: Amélioration - Page non trouvée sur les environnements
* Une nouvelle "page non trouvée" a été créée pour les environnements, afin que l'utisateur comprenne plus facilement l'origine de l'erreur et donne les solutions les plus courantes.

## 17/10/2023: Fonctionnalité - Magic links
* Nouvelle fonctionnalité permettant d'avoir une url qui réouvre l'environnement s'il était en pause.

## 13/09/2023: Fonctionnalité - Module de démo
* Ajout d'un module de démonstration permettant de tester la solution en conditions réelles depuis la page d'accueil du site.

## 22/08/2023: Correctif
* Fix d'un bug affectant le calcul du nombre d'environnements ouverts dans un espace en cas d'erreur à l'ouverture d'un environnement.

## 30/06/2023: Amélioration - Internationalisation
* Refonte de la page d'accueil.
* Internationalisation complète de l'applicatif pour les langues anglaise et française.

## 13/06/2023: Amélioration - Remise en marche des environnements
* Les erreurs pouvant survenir pendant la remise en marche d'un environnement en pause ne sont plus bloquantes pour sa réouverture.

## 08/06/2023: Correctifs
* Correction d'un problème affectant les utilisateurs de l'interface web de VSCode, dont les environnements se trouvaient mis en pause de manière intempestive. 
* Correction d'un problème affectant les envirronements mis en pause après l'ajout d'un nouveau dépot dans la configuration du projet.

## 05/06/2023: Amélioration - Mise en pause / remise en marche
* Modification de l'architecture utilisée pour la mise en pause, permettant de diviser par 5 le temps sur la mise en pause, et par 4 pour la remise en marche.

## 22/05/2023: Améliorations - Modifications des volumes des images préconfigurées
* L'interface de paramétrage de la virtualisation permet désormais de modifier/ajouter/supprimer des volumes au sein du mode "Utiliser les images préconfigurées de Protocode".

## 05/05/2023: Améliorations - Utilisateur rootless et images préconfigurées
* L'utilisateur rootless. (protocode) a désormais l'id 1000, afin de simplifier la gestion des droits avec de nombreuses images docker partageant cet id.
* Toutes les images préconfigurées ont désormais l'id 1000 pour l'utilisateur du processus principal (www-data pour php par exemple).
* Les images de Prestashop et de Wordpress ont été améliorées pour s'intégrer nativement dans l'écosystème Protocode (versions "plug-n-play").
* Les images node 20, php 8.2, adminer et maildev ont été ajoutées dans les images préconfigurées.
* Fix d'un bug empêchant la préconstruction d'image dans les dépôts ou la version de docker-compose utilisée était la V1.

## 21/04/2023: Correctifs - Lien de prévisualisation sur les environnements mis en pause
* Correction liée à l'ajout de la dissociation des environnements vis-à-vis des configurations de dépots. Les liens de prévisualisation n'étaient plus affichés sur l'interface web pour les environnements remis en marche.

## 20/04/2023: Amélioration - Remise en marche des environnements
* La remise en marche des environnements est désormais dissociée des configurations de dépots. Cela évite que les modifications de configuration crée des erreurs bloquant la remise en marche des environnements mis en pause.

## 04/04/2023: Correctif
* Correction d'un bug lié à l'ajout des environnements rootless. Les extensions vcode n'étaient plus installées avec la commande `code --install-extension`.

## 01/04/2023: Modification du plan tarifaire
* Retrait des plans pay as you go individuals et pay as you go entreprise, et du plan developer.
* Modification du plan Starter, devenant gratuit, offrant 50 crédits mensuels, et sans dépassement possible.
* Ajout du pack Pro, à 9€ par mois, offrant 100 crédits mensuels, et dépassement payé au nombre de crédits consommés (0.18€/crédit). 

## 23/03/2023: Fonctionnalité - Ajout d'un nouveau hook de cycle de vie
* Ajout d'un nouveau hook permettant d'ajouter du traitement avant la mise en veille d'un environnement.

## 15/03/2023: Fonctionnalité- Intégration du feedback portal de Userback
* Deux interfaces sont désormais disponibles. L'une pour émettre des idées d'évolution, et l'autre pour voir la roadmap publique.

## 06/03/2023: Fonctionnalité - Environnement sans utilisateur root
* Au niveau de la configuration des projets, il est désormais possible de choisir l'utilisateur par défaut au sein des environnements. Soit l'utilisateur super-privilégié "root", soit un utilisateur non privilégié "protocode" (qui dispose cependant du pouvoir d'utiliser "sudo" sans mot de passe pour toute commande nécessitant des accès root).

## 16/02/2023: Correctifs & Améliorations
* Fix de l'erreur "Git Unsafe Repository"
* Amélioration du processus de build. Identification exacte des images à construire, et construction de ces images seules. Plus de pull des autres images du fichiers docker-compose. Le processus de pré-construction n'est plus obligatoire si toutes les images sont déjà préconstruites.

## 14/02/2023: Amélioration
* L'ouverture dans VSCode local se fait désormais dans une nouvelle fenêtre

## 13/02/2023: Correctifs
* Fix de l'erreur request timeout lors de la récupération de logs lorsque très volumineux
* Fix variable ENVIRONMENT_URL non définies dans une connexion ssh

## 10/02/2023: Correctifs & changements mineurs
* Fix de l'erreur retournée à la mise en pause des environnement lors de la compression de fichiers larges modifiés en cours de processus.
* Version par défaut de docker-compose passe de la v1 à v2
* Ajout des liens vers le changelog et le statut des service

## 09/02/2023: Fonctionnalités - IDEs JetBrains
* Ajout de la possibilité de se connecter aux IDEs de Jetbrains: CLion, GoLand, IntelliJ, PhpStorm, PyCharm, Rider, RubyMine, WebStorm.
* Refonte des menus et boite de dialogue propres aux opérations sur les environnements, le code, la prévisualisation et la gestion de projet.

## 03/02/2023: Correctifs - Stabilité des services
* Amélioration de la gestion automatisée de la flotte serveur.
* Ajout de la fonctionnalité de mise en quarantaine des serveurs défectueux.
* Amélioration des scripts de vérification de l'état des serveurs.
* Amélioration du processus de kill des processus lancés.
* Fix de l'affichage des caractères unicode non interprétés dans la modale de visualisation des processus.

## 31/01/2023: Nouvelle offre tarifaire
* Ajout des nouvelles offres tarifaires dans la souscription.
* Refactoring de la page facturation.

## 30/01/2023: Améliorations - Optimisation des services
* Diminution du temps de démarrage des environnements (3.5s vs. 20s).
* Ajout de la mise en cache des fichiers non versionnés lors du lancement d'un cycle complet. Permet la division par 4 des temps d'ouverture de nouveaux environnements.
* Modification des outils de compression pour la mise en veille et la remise en marche des environnement, permettant de diviser par 5 la taille des archives.
* Ajout de la possibilité d'installer les extensions vscode dans les scripts d'initialisation.

## 12/12/2022: Style - Refonte du site web:
* Nouvelle arborescence de pages.
* Utilisation des polices et des couleurs officielle de la charte graphique.

## 21/10/2022: Amélioration - Synchronisation VSCode web et local
* Ajout de la synchronisation des extensions et des préférences entre VSCode web et VSCode local

## 13/10/2022: Correctif
* Fix du problème de communication entre les conteneurs docker de dépôts git différents (projets multi-dépôts).

## 05/10/2022: Fonctionnalité - Redémarrage des environnements
* Ajout de l'option "Redémarrer" un environnement ouvert.

## 30/09/2022: Fonctionnalité - Mise en pause des environnements
* Ajout de l'option "Mettre en pause" un environnement ouvert.
* Ajout de l'option "Remettre en marche" un environnement ouvert.
* Ajout du champ "Temps d'inactivité avant mise en sommeil" dans la page détails d'un projet.

