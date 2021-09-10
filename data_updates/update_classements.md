---
layout: default
title: Installations et classements
permalink: /data/classements
parent: Mise à jour des données
nav_order: 1
---

# Mise à jour des installations et des classements

Les classements sont mis à jour à partir des extractions S3IC. Pour effectuer la mise à jour, il faut générer des fichiers CSV bien formattés à partir des fichiers CSV bruts puis les ajouter au dépôt `envinorma-web` et les mettre à jour en production. En détails, voici les différentes étapes :

1. Placer les CSV bruts issus de l'extraction S3IC dans un dossier en local
1. Cloner le dépôt [https://github.com/Envinorma/envinorma-web](https://github.com/Envinorma/envinorma-web)
1. Générer les nouveaux fichiers CSV avec ce [script](https://github.com/Envinorma/data-tasks#mettre-%C3%A0-jour-les-classements-et-les-installations-%C3%A0-partir-de-lextraction-s3ic). Au préalable, remplacer `$INPUT_FOLDER` par le chemin vers le dossier contenant les fichiers extraits au point `1.`, et `$OUTPUT_FOLDER` par le chemin vers le dossier dans lequel générer les CSV formatés, à savoir le dossier `db/seeds` du depôt `envinorma-web` cloné au point `2.`
1. L'opération précédente a généré les fichiers `installations_*.csv` et `classements_*.csv` dans le dossier `envinorma-web/db/seeds`. Les commiter et les pusher
1. Déployer l'app (cf [https://github.com/Envinorma/envinorma-web/README.md](https://github.com/Envinorma/envinorma-web/README.md)), puis seeder les installations et les classements dans l'application Envinorma, en exécutant la commande suivante dans la console rails de production :

```ruby
DataManager.seed_installations_and_associations
```
