---
title: 'La mise en pause ne se déclenche pas'
---

Alors que la configuration du projet est paramétrée pour qu'un environnement soit [automatiquement mis en pause](/configurer-son-projet/mise-en-sommeil#declenchement-automatique) au bout d'un certain laps de temps d'inactivité, mon environnement reste continuellement ouvert.

Pour rappel, est considéré comme inactif un environnement qui ne dispose d'aucune connexion ssh et http active. Si un environnement ne se met pas en veille, c'est en principe soit parce qu'un IDE y est toujours connecté, ou que quelqu'un consulte une url de prévisualisation. Vérifiez donc qu'aucun IDE n'est connecté, et qu'aucune autre personne (ou service tiers) n'est en train de consulter les urls exposés par l'environnement.

Si le problème persiste, n'oubliez pas que vous pouvez tout de même déclencher manuellement la mise en pause, et [contactez le support](/ressources-support/contact-support).