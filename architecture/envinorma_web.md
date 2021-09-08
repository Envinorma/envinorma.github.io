---
layout: default
title: Architecture de envinorma-web
permalink: /architecture/envinorma_web
parent: Architecture
nav_order: 2
---


## Architecture de envinorma web

### Les données
Pour fonctionner l'application nécessite un certains nombres de données externes, liées aux installations et à la règlementation.
Vous trouverez dans [ce dossier](https://github.com/Envinorma/data-tasks) les différentes tâches de préparation de la donnée. Elle est ensuite incorporée dans l'application à l'aide du `DataManager`.

```
DataManager.seed_installations_and_associations(true)
#permet de seeder les installations ainsi que leurs classements et arrêtés préfectoraux associés

DataManager.seed_ams
#permet de seeder les arrêtés ministériels
```

> La donnée est simplement supprimée puis recréée.

> On utilise la gem `after_party` pour lancer des tâches au moment du déploiement. ex: lorsque que l'on met en production un nouveau lot d'arrêtés ministériels

![le schéma de la donnée](/assets/schema.png)

> La donnée des tables `installations`, `classements`, `APs` et `AMs` sont seedées à partir de scripts et ne sont pas modifiées directement par l'utilisateur. L'utilisateur peut toutefois créer de nouvelles installations (à partir de 0 ou en dupliquant des installations existantes) et y ajouter ou modifier leurs classements.
