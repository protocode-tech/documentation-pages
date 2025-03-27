---
title: 'Projet WordPress'
taxonomy:
    category:
        - docs
---

Voici un exemple de projet WordPress configuré avec Protocode :

[https://github.com/protocode-tech/wordpress-template](https://github.com/protocode-tech/wordpress-template)

## Contenu du projet

Il contient un répertoire `.protocode` contenant toute la configuration :

[prism classes="language-text" highlight="2,3,4,5,6,7"] 
└── wordpress-template/
   ├── .protocode/
   │  └── .env
   │  └── docker-compose.yml
   │  └── Dockerfile
   │  └── lifecycle/
   │    └── postUp.sh
   │ ... Rest of the files
[/prism]

* Le fichier **.env** contient les variables utilisées par docker-compose.
* Le fichier **docker-compose.yml** contient la configuration de docker-compose, il crée un conteneur app basé sur Php 8.1, l'expose publiquement, un conteneur pour la base de données, gère la synchronisation des fichiers entre conteneur et machine hôte, et ajoute les [alias Docker](/configurer-son-projet/alias-docker) les plus pertinents.
* Le fichier **Dockerfile** décrit les étapes de construction du conteneur app, installe toutes les dépendances (php, apache, composer...).
* Le dossier **lifecycle** contient les scripts d'initialisation du projet. Le fichier preUp.sh s'occupe de créer les fichiers de configuration attendus par WordPress, règle les éventuels problèmes de droits.

## Comment l'utiliser

Dans un projet similaire, vous pouvez soit :
- **Versionner les fichiers dans votre dépôt et y faire référence dans la configuration du dépôt sur Protocode**. Récupérez le contenu de ce répertoire et le versionnez au sein de votre projet, puis dans la configuration de la virtualisation du dépôt sur Protocode, sélectionnez "Utiliser le fichier docker-compose au sein du dépôt", précisez ensuite l'emplacement ".protocode/docker-compose.yml". Ensuite, dans la partie "Initialisation", au niveau de "Avant la construction des conteneurs", placez ".protocode/lifecycle/preUp.sh".
- **Copier le contenu des fichiers dans la configuration du dépôt sur Protocode sans les versionner au projet**. Dans la configuration de la virtualisation du dépôt sur Protocode, sélectionnez "Créer un fichier docker-compose personnalisé", collez le contenu de .protocode/docker-compose.yml dans le champ du formulaire. Ensuite, dans la partie "Initialisation", au niveau de "Avant la construction des conteneurs", collez le contenu de ".protocode/lifecycle/preUp.sh".
