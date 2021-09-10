---
layout: default
title: Nomenclature
permalink: /data/nomenclature
parent: Mise à jour des données
nav_order: 4
---

# Mise à jour des références de classements (nomenclature)

Les classements sont mis à jour à partir des extractions géorisques. Pour effectuer la mise à jour, il faut :

1. Placer les CSV bruts issus de l'extraction Géorisques dans un dossier en local
1. Cloner le dépôt [https://github.com/Envinorma/envinorma-web](https://github.com/Envinorma/envinorma-web)
1. Générer le fichier `classement_references.csv` avec la librairie data-tasks dans le dossier `db/seeds` du dépot `envinorma-web`, comme expliqué [ici](https://github.com/Envinorma/data-tasks#g%C3%A9n%C3%A9rer-la-nomenclature-classement_referencescsv-%C3%A0-partir-de-lextraction-g%C3%A9orisques).\
   (Remplacer pour cela `$INPUT_FOLDER` par le chemin vers le dossier contenant les fichiers extraits au point `1.`, et `$OUTPUT_FOLDER` par le chemin vers le dossier dans lequel générer les CSV formatés, à savoir le dossier `db/seeds` du depôt `envinorma-web` cloné au point `2.`)
1. Maintenant que le fichier `classement_references.csv` a été généré dans le dossier `envinorma-web/db/seeds`, le commiter et le pusher
1. Déployer l'app (cf [https://github.com/Envinorma/envinorma-web/README.md](https://github.com/Envinorma/envinorma-web/README.md)) puis mettre à jour ces références dans l'application Envinorma, en exécutant la commande suivante dans la console rails :

```ruby
DataManager.seed_classement_references
```
