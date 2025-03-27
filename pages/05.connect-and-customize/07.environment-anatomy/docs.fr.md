---
title: 'Anatomie d''un environnement'
taxonomy:
    category:
        - docs
---

## Arborescence des fichiers

Le **répertoire par défaut** d'un environnement est `/var/environment`. Vous y êtes automatiquement positionné lorsque vous vous connectez en SSH avec votre IDE ou votre terminal, et lorsque vous ouvrez l'interface web de Visual Studio Code.

À l'intérieur du répertoire `/var/environment`, se trouvent les différents dépôts qui composent votre projet :

[prism classes="language-text" highlight="2,3"] 
└── /var/environment/
   ├── my-repository/
   └── my-other-repository/
[/prism]

Lorsqu'un environnement est démarré, Protocode génère un dossier `.protocode-runtime` qui est stocké à la racine de chaque dépôt du projet. Ce dossier contient tous les fichiers nécessaires au fonctionnement de l'environnement:

[prism classes="language-text" highlight="3"] 
└── /var/environment/
   ├── my-dépôt/
   │   └── .protocode-runtime/
   │      └── .env 
   │      └── docker-compose.yml
   │      └── lifecycle/
   │         └── prePull.sh
   │         └── postPull.sh
   │         └── preUp.sh
   │         └── postUp.sh
   │         └── preFreeze.sh
   │         └── preDown.sh
   │      └── version
   │ ... Rest of my files
[/prism]

Ces fichiers ont les rôles suivants :

* **`.env`** : ce fichier contient toutes les variables d'environnement saisies dans la configuration du dépôt. Ces variables seront injectées dans chaque commande de `docker-compose`.

* **`docker-compose.yml`** : c'est le fichier de configuration généré par Protocode à destination de Docker Compose. C'est lui qui sera pris en compte lorsque vous ferez appel à `docker-compose` depuis la racine d'un dépôt (même si un autre fichier `docker-compose.yml` se trouve au même niveau). Vous pourrez donc, par exemple, stopper tous les conteneurs avec une commande telle que :

[prism classes="language-bash command-line" cl-prompt="$"]
cd my-dépôt # Je me déplace du répertoire par défaut au dépôt
docker-compose down
[/prism]

Puis éventuellement modifier certaines valeurs du fichier de démarrage (`.protocode-runtime/docker-compose.yml`), et relancer les conteneurs en lançant : 

[prism classes="language-bash command-line" cl-prompt="$"]
cd /var/environment/my-dépôt
docker-compose up -d
[/prism]

* **`lifecycle`** : c'est un dossier qui contient tous les scripts d'initialisation de l'environnement créés au démarrage de l'environnement, et qui seront joués pendant les différentes [étapes de son cycle de vie](/configurer-son-projet/scripts-dinitialisation).

* **`version`** : c'est un fichier contenant des informations de version nécessaires au fonctionnement.

!! Le dossier **.protocode-runtime est ignoré globalement** dans Git et n'apparaîtra pas lorsque vous afficherez les modifications au sein de chacune des sources.  
!! **Il est important de ne pas le supprimer** pour le bon fonctionnement de notre système.

## Outils préinstallés

Un environnement est une instance Debian 11 qui embarque un certain nombre d'outils nécessaires à son fonctionnement, notamment :

- **Pour la virtualisation** : Docker, Docker Compose
- **Pour le versionning des sources** : Git, Git LFS
- **Pour le terminal** : Bash, Zsh
- **Pour l'édition de fichiers** : Vim, Nano
- **Pour la récupération de fichiers** : Curl, Wget

!!! Vous pouvez selon vos besoins utiliser ces outils ou en installer d'autres (par exemple, `make`). Cependant, ne perdez pas de vue qu'un environnement est une machine destinée à faire tourner des conteneurs Docker. Il est donc par exemple inutile d'y installer Node.js. On préfèrera ajouter un conteneur faisant tourner Node.js.

## Conteneurs Docker

Votre environnement est comme un poste de travail distant faisant tourner des conteneurs avec Docker. Lorsque vous vous connectez, vous êtes positionné dans le répertoire par défaut et à l'extérieur de vos conteneurs. Si vous ouvrez un terminal et entrez la commande suivante pour voir la liste de vos conteneurs :

[prism classes="language-bash command-line" cl-prompt="$"]
docker ps
[/prism]

Vous verrez un retour du type : 

[prism classes="language-bash"]
CONTAINER ID   IMAGE              COMMAND                  CREATED       STATUS       PORTS                 NAMES
3a70f7c8c765   node:16            "docker-entrypoint.s…"   10 days ago   Up 10 days   80/tcp                protocode-web_app
6703eddacc5d   protocode-api_app  "docker-php-entrypoi…"   3 weeks ago   Up 3 weeks   80/tcp, 9000/tcp      protocode-api-app
82c3d52d0e50   mysql:8.0          "docker-entrypoint.s…"   3 weeks ago   Up 3 weeks   3306/tcp, 33060/tcp   protocode-api-database
[/prism]

Comme vous êtes dans le répertoire par défaut, et non à l'intérieur d'un de vos dépôts, toute commande `docker-compose` déboucherait sur une erreur, puisque Docker Compose ne trouverait pas de fichier de configuration dans le répertoire par défaut. Il vous faut donc tout d'abord vous déplacer, pour ensuite lancer une commande `docker-compose` :

[prism classes="language-bash command-line" cl-prompt="$"]
cd my-dépôt
docker-compose exec app bash # Pour cet exemple, j'entre dans le terminal d'un conteneur
[/prism]

En somme, ce n'est pas différent d'une utilisation de Docker en local.

## Git

Git est installé au niveau de l'environnement, et a été paramétré pour communiquer avec les différents dépôts qui composent votre projet, afin de récupérer les sources et pousser des modifications.

**Par défaut, chaque dépôt est positionné sur la branche sélectionnée comme "Par défaut"** dans sa configuration (voir [Ajout de source](/configurer-son-projet/ajout-depot-git)). Il revient au développeur, comme en local, de créer sa propre branche de travail sur chaque dépôt et de se mettre à jour (via `git pull` / `git rebase` selon vos habitudes).

! Pour éviter que des modifications ne soient poussées sur la branche principale d'un dépôt, nous vous invitons à veiller à ce qu'elle soit protégée du côté de votre hébergeur de source, et ne puisse être modifiée qu'au travers d'une fusion.
