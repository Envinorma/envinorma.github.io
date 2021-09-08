---
layout: default
title: Nomenclature
permalink: /data/nomenclature
parent: Mise à jour des données
nav_order: 4
---

# Mise à jour des références de classements (nomenclature)

Les classements sont mis à jour à partir des extractions géorisques. Pour effectuer la mise à jour, il faut :

1. Générer le fichier `classement_references.csv` avec la librairie data-tasks dans le dossier `envinorma-web/db/seeds`, comme expliqué [ici](https://github.com/Envinorma/data-tasks#g%C3%A9n%C3%A9rer-la-nomenclature-classement_referencescsv-%C3%A0-partir-de-lextraction-g%C3%A9orisques)
2. Seeder ces références dans l'application Envinorma, en exécutant la commande suivante dans la console rails :

```ruby
DataManager.seed_classement_references
```
