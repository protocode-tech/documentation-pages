---
title: 'Préconstruction Docker'
taxonomy:
    category:
        - docs
slug: preconstruction-docker
media_order: 'docker_prebuild_FR.png,docker_prebuild_ok_FR.png'
---

Lorsque la configuration saisie utilise des images Docker personnalisées, Protocode impose que les images soient préconstruites et stockées dans notre registry, afin de démarrer les environnements le plus rapidement possible.

## Lancement de la préconstruction

Si la préconstruction est requise, Protocode vous affichera l'invitation suivante :

![docker_prebuild_FR](docker_prebuild_FR.png?style=max-width:35rem;)

Il vous suffit de cliquer sur le bouton **"Préconstruire"** pour lancer le processus. Les logs de sortie s'afficheront alors pour que vous puissiez voir où cela en est ainsi que les éventuelles erreurs pouvant survenir.

Si la préconstruction s'est passée avec succès, un message apparaît et le processus est noté comme **"Terminé"**.

![docker_prebuild_ok_FR](docker_prebuild_ok_FR.png?style=max-width:35rem;)

## Modification de la configuration et reconstruction

Si vous modifiez les fichiers impliqués dans la configuration Docker du projet, il vous faudra relancer ce processus pour reconstruire des images à jour. Il n'y a aucune automatisation. Cette mise à jour affectera tous les environnements nouvellement ouverts ou remis en marche, mais pas les environnements déjà ouverts (si nécessaire, mettez-les en pause et remettez-les en marche).
