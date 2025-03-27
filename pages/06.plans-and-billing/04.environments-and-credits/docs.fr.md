---
title: 'Type d''environnements et consommation de crédits'
taxonomy:
    category:
        - docs
media_order: billing_consumption_FR.png
---

Les environnements ouverts consomment des crédits. Le nombre de crédits qu'ils consomment à l'heure dépend des ressources allouées. Par défaut, les environnements sont paramétrés sur le profil minimum ("Small"), qui consomme un crédit par heure. En fonction des besoins d'un projet, il est possible que le minimum ne suffise pas, auquel cas il est possible d'[augmenter les ressources allouées](/configurer-son-projet/allouer-des-ressources). Les différents profils sont les suivants:

| Nom    | CPU      | Ram    | Crédits / h    | Par défaut |
|--------|----------|--------|----------------|------------|
| Small  | 2 coeurs | 4 Go   | 1 crédit / h   | Oui        |
| Medium | 4 coeurs | 8 Go   | 2 crédits / h  | Non        |
| Large  | 8 coeurs | 16 Go  | 4 crédits / h  | Non        |
| XLarge | 16 coeurs| 32 Go  | 8 crédits / h  | Non        |
| XXLarge| 32 coeurs| 64 Go  | 16 crédits / h | Non        |

!!! Exemple concret: Un environnement Medium ouvert 7 heures consommera donc 14 crédits.

Les formules d'abonnement accordent mensuellement un nombre de crédits (actuellement de 50 à 350 crédits mensuels). La consommation de crédits par les environnements se soustrait à ce volume en continu. Vous pouvez consulter l'état de votre consommation en cours à tout moment en vous rendant dans "Facturation", et en consultant le bloc "Consommation en cours":

![billing_consumption_FR](billing_consumption_FR.png?style=max-width:25rem;)

Les formules accordent un nombre de crédits mensuels qui ne sont pas reportés s'ils ne sont pas consommés. Au début de chaque nouveau cycle de facturation, le nombre de crédits disponible est réinitialisé.
