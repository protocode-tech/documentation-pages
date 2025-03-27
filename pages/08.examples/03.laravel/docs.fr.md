---
title: 'Projet Laravel'
taxonomy:
    category:
        - docs
slug: projet-laravel
---

Voici un exemple de projet Laravel configuré avec Protocode :

[https://github.com/protocode-tech/laravel-template](https://github.com/protocode-tech/laravel-template)

## Contenu du projet

Il contient un répertoire `.protocode` contenant toute la configuration :

[prism classes="language-text" highlight="2,3,4,5,6"] 
└── laravel-template/
   ├── .protocode/
   │  └── docker-compose.yml
   │  └── lifecycle/
   │    └── preUp.sh
   │    └── postUp.sh
   │ ... Rest of the files
[/prism]

* Le fichier **docker-compose.yml** contient la configuration de docker-compose, il crée un conteneur app basé sur PHP 8.2, l'expose publiquement, un conteneur pour la base de données, gère la synchronisation des fichiers entre conteneur et machine hôte, et ajoute les [alias Docker](/configurer-son-projet/alias-docker) les plus pertinents.
* Le dossier **lifecycle** contient les scripts d'initialisation du projet. Le fichier preUp.sh s'occupe de créer les fichiers d'environnement attendus par Laravel et d'installer l'extension officielle Intelephense pour VSCode, et le fichier postUp.sh installe les dépendances avec Composer.

## Comment l'utiliser

Dans un projet similaire, vous pouvez soit :
- **Versionner les fichiers dans votre dépôt et y faire référence dans la configuration du dépôt sur Protocode**. Récupérer le contenu de ce répertoire et le versionner au sein de votre projet, puis dans la configuration de la virtualisation dépôt sur Protocode, sélectionnez "Utiliser le fichier docker-compose au sein du dépôt", précisez ensuite l'emplacement ".protocode/docker-compose.yml". Ensuite, dans la partie "Initialisation", au niveau de "Avant la construction des conteneurs", placez ".protocode/lifecycle/preUp.sh", et au niveau de "Après la construction des conteneurs", placez ".protocode/lifecycle/postUp.sh".
- **Copier le contenu des fichiers dans la configuration du dépôt sur Protocode sans les versionner au projet**. Dans la configuration de la virtualisation du dépôt sur Protocode, sélectionnez "Créer un fichier docker-compose personnalisé", collez le contenu de .protocode/docker-compose.yml dans le champ du formulaire. Ensuite, dans la partie "Initialisation", au niveau de "Avant la construction des conteneurs", collez le contenu de ".protocode/lifecycle/preUp.sh", et au niveau de "Après la construction des conteneurs", celui de ".protocode/lifecycle/postUp.sh".
