---
title: 'Paramétrer son projet'
taxonomy:
    category:
        - docs
slug: parametrer-son-projet
---

Dans la section "Projets", cliquez en haut à droite sur le bouton "Créer" et remplissez les informations demandées. Vous êtes ensuite redirigé vers la page d'administration du projet, dans la section "Configuration".  

## Ajout d'une source  

Dans le bloc "Dépôts Git du projet", cliquez sur le bouton "Ajouter", puis saisissez l'adresse du dépôt. Copiez la clé SSH générée et ajoutez-la en tant que clé de déploiement avec les droits en écriture sur votre dépôt. Cliquez sur "Continuer", sélectionnez la branche par défaut, puis cliquez à nouveau sur "Continuer".  

## Virtualisation  

Vous êtes redirigé vers la partie _Virtualisation_. Cliquez sur "Lancer l'IA" et attendez jusqu'à ce que la configuration Docker soit générée (2 minutes maximum). Vous êtes ensuite invité à construire les images Docker du projet. Le processus est lancé automatiquement, attendez jusqu'à la fin du traitement (5 minutes maximum).  

## Initialisation  

Une fois la préconstruction terminée, vous êtes redirigé vers la partie _Initialisation_ pour lancer une mise en cache. Le processus est lancé automatiquement, attendez jusqu'à la fin du traitement (2 minutes maximum). Votre projet est désormais entièrement paramétré, vous pouvez cliquer sur "Fermer" en bas à droite. 