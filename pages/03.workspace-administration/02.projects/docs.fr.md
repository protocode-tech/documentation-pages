---
title: Projets
visible: true
taxonomy:
    category:
        - docs
---

Le projet est l'objet le plus large. Il englobe les dépôts GIT, les membres de l'équipe, les tâches et leur assignation.  
Sans parler de l'ajout des dépôts (qui est décrit dans la partie [Configuration](/configurer-son-projet/ajout-depot-git)), nous allons ici décrire comment gérer un projet dans Protocode d'un point de vue organisationnel.  

## Administrer les membres de l'équipe

Toute personne ajoutée en tant que membre de l'espace de travail peut être ajoutée comme membre d'un projet. Pour cela, il vous suffit de vous rendre sur la fiche d'un projet, de cliquer sur l'onglet "Équipe", et enfin de cliquer sur le bouton "Créer". Au clic sur le bouton, une modale s'ouvre, vous invitant à sélectionner un membre de l'espace de travail, un créneau de dates pendant lequel il intervient (c'est optionnel), et un profil. Le système de profil au sein d'un projet est très similaire à celui propre aux [membres d'un espace](/administrer-son-espace/membres).  

| Nom | Description |  
| --- | --- |  
| **Manager** | C'est le profil accordant le plus de droits sur le projet. L'utilisateur peut administrer et voir tous les membres, les dépôts, les tâches et leurs assignations. |  
| **Développeur** | C'est un profil intermédiaire qui donne à l'utilisateur le droit de voir tous les membres, les dépôts, les tâches et leurs assignations, mais aucun droit d'administration. C'est suffisant si le rôle de l'utilisateur se cantonne à démarrer un environnement, coder et mettre à jour le statut d'une tâche. |  
| **Invité** | C'est le profil le plus bas, qui donne à l'utilisateur uniquement le droit de voir les tâches qui lui sont assignées. C'est le droit qui s'accorde le mieux à la présence d'un tiers externe à l'entreprise dans la vie du projet. |  

!!! De la même manière que pour les membres de l'espace de travail, il est possible de modifier manuellement les droits accordés en cochant/décochant les droits affichés dans la modale. On peut notamment imaginer qu'un développeur puisse modifier les dépôts pour relancer une préconstruction, ou créer des tâches pour d'autres.  

## Administrer les tâches

À l'intérieur d'un projet, il est possible de créer autant de tâches que nécessaire. Celles-ci se retrouvent dans la fiche d'un projet, dans l'onglet "Tâches".  

Chaque tâche créée dispose d'un certain nombre d'informations que l'on peut dissocier en deux groupes :  
* **Les informations relatives à l'identification de la tâche**. Il en va ainsi pour le nom, la description et le flag (fonctionnalité/bug) de la tâche.  
* **Les informations relatives à la gestion de projet**. Ce seront notamment les états (ouvert/fermé), la priorité (de basse à urgente), les dates prévues de début et de fin, le temps prévu pour réaliser le travail, et la personne en charge de la supervision de la tâche (le "Superviseur").  

Par défaut, une tâche créée sera identifiée comme "Non assignée". Autrement dit, elle n'a été confiée à aucun membre de l'équipe. Pour le faire, il faudra se rendre sur la fiche de la tâche (en cliquant sur son nom depuis la liste des tâches), puis cliquer sur le bouton "Assigner". Une modale s'ouvre et propose de sélectionner l'un des membres de l'équipe. Une fois l'assignation créée, la tâche dispose alors d'un statut "En attente". Parallèlement, la personne assignée à cette tâche recevra un e-mail de notification pour l'en informer. Lorsqu'elle se connectera à Protocode, la tâche apparaîtra dans "Mes tâches", et elle pourra démarrer un environnement spécifique à celle-ci.  

## Cycle de vie d'une tâche

Dès qu'une personne démarre un environnement, le statut de la tâche correspondante est automatiquement mis à jour, et passe à "En cours". La progression du travail est aussi automatiquement mise à jour, et passe à 10%.  

Lorsque son travail sera fini, il est ensuite possible de modifier le statut de la tâche à "À tester", la progression est automatiquement passée à 80%. Le superviseur (s'il y en a un) recevra un e-mail de notification, et la tâche disparaîtra de la liste des tâches à traiter pour le développeur. Elle apparaîtra pour le superviseur dans "Mes supervisions".  

Le superviseur pourra ensuite modifier le statut à "En validation" pour accuser bonne réception. Puis, au terme de son test, il pourra passer la tâche à "Terminée" ou à "Rejetée".  

Si la tâche est terminée, la progression est automatiquement passée à 100%, et il peut clôturer l'environnement. Si des changements n'ont pas été validés ou poussés, le système lui proposera de le faire.  

Si la tâche est rejetée, le développeur reçoit une notification pour l'en informer et la tâche réapparaît dans "Mes tâches". Il modifiera alors la tâche pour la passer à "En cours", puis à nouveau à "À tester" lorsque les retours auront été traités.  

## Portée d'une tâche

Vous êtes totalement libre de définir la portée des tâches que vous créez. Soit vous les définissez de manière précise et ciblée, ce qui débouchera pour chacune à des environnements distincts. Soit vous pouvez augmenter leur portée, et définir des tâches correspondant à un sprint complet, ou même à la vie complète d'un projet (ce qui revient à utiliser une tâche comme un poste de travail permanent).  
