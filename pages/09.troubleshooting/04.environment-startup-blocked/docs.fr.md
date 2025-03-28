---
title: 'Démarrage d''environnement bloqué'
media_order: 'process_show_FR.png,process_create_server.png,process_error_FR.png'
---

## Processus bloqué

Après avoir cliqué sur le bouton **"Démarrer"** d'un environnement, le processus semble figé à une étape et ne progresse plus après plusieurs minutes.


### Vérifier l’état du processus 

Commencez par afficher les logs pour voir **à quelle étape** le processus est bloqué et quelles sont les **sorties de commande**.

![process_show_FR](process_show_FR.png?style=max-width:25rem;)

### Les commandes bloquantes

Le cas le plus fréquent est une **commande bloquante** dans le cycle de vie du projet, comme la compilation d’une application **JavaScript**. 

- Si une commande **exécute un processus en continu**, le démarrage restera bloqué.  
- **Solution :**  
  - Interrompez le démarrage.  
  - Supprimez la commande du script exécuté au lancement.  
  - Déplacez-la dans le fichier **docker-compose** en tant que [commande du service](https://docs.docker.com/reference/compose-file/services/#command) :

[prism classes="language-yaml line-numbers" highlight="12"]
version: '3.8'
services:
  app:
    image: node:16
    volumes:
      - .:/app
    working_dir: /app
    ports:
      - '80'
    environment:
      VIRTUAL_HOST: "app-my-repository.${ENVIRONMENT_URL}"
    command: npm run dev # La commande ne bloquera plus le cycle de vie
[/prism]

👉 **Alternative** : Exécutez la commande manuellement depuis le terminal de votre IDE une fois l’environnement lancé.

### La provision d'un serveur

Si un grand nombre d’utilisateurs lancent des environnements en même temps, il se peut que **Protocode doive provisionner un nouveau serveur**.
Cette étape dure en moyenne 90 secondes.

![process_create_server](process_create_server.png?style=max-width:35rem;)

Si après 5 minutes le serveur n'est toujours pas prêt, [contactez le support](/ressources-support/contact-support).

## Processus en erreur

Si après avoir cliqué sur **"Démarrer"**, le processus s’arrête brutalement et **une icône rouge** apparaît, cela signifie qu'**une erreur a empêché le lancement**.

![process_error_FR](process_error_FR.png?style=max-width:25rem;)

Affichez les logs en cliquant sur l’icône rouge pour identifier la source du problème.

### Erreur dans une commande du cycle de vie

L'erreur la plus fréquente est due à une commande incorrecte dans les étapes du cycle de vie.

Consultez les logs, identifiez l'erreur et corrigez le script correspondant.

### Problème avec le registry Docker

Si le **registry** (service qui stocke les images Docker du projet) est temporairement inaccessible pour **maintenance**, le démarrage peut échouer.

* **Vérifiez son statut** l'[état des services](https://status.protocode.tech/)
* Si le service est **en rouge**, attendez quelques minutes et réessayez.

Si le problème persiste, [contactez le support](/ressources-support/contact-support).
