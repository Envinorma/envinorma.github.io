---
layout: default
title: Installations et classements
permalink: /data/classements
parent: Mise à jour des données
nav_order: 1
---

# Mise à jour des installations et des classements

Les classements sont mis à jour à partir des extractions S3IC. Pour effectuer la mise à jour, il faut :

1. Générer les fichiers `installations_all.csv` et `classements_all.csv` avec la librairie data-tasks dans le dossier `envinorma-web/db/seeds`, comme expliqué [ici](https://github.com/Envinorma/data-tasks#mettre-%C3%A0-jour-les-classements-et-les-installations-%C3%A0-partir-de-lextraction-s3ic)
2. Seeder les installations et les classements dans l'application Envinorma, en exécutant la commande suivante dans la console rails :

```ruby
DataManager.seed_installations_and_associations
```
