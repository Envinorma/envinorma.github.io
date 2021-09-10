---
layout: default
title: Arrêtés préfectoraux
permalink: /data/ap
parent: Mise à jour des données
nav_order: 2
---

# Mise à jour des arrêtés préfectoraux à partir de l'extraction Géorisques

_Pour exécuter les scripts, les identifiants OVH et Heroku sont nécessaires. Ils peuvent être récupérés via Resana sur demande à un responsable du projet._

## 1. Générer `aps_*.csv`

1. Placer les CSV bruts issus de l'extraction Géorisques dans un dossier en local
1. Cloner le dépôt [https://github.com/Envinorma/envinorma-web](https://github.com/Envinorma/envinorma-web)
1. Pour générer les CSV formatés `aps_*.csv`, utiliser la librairie data-tasks et suivre ces [instructions](https://github.com/Envinorma/data-tasks#mettre-%C3%A0-jour-les-fichiers-apscsv-%C3%A0-partir-de-lextraction-g%C3%A9orisques) pour générer le fichier `aps_*.csv` dans `envinorma-web/db/seeds`.\
   (remplacer pour cela `$INPUT_FOLDER` par le chemin vers le dossier contenant les fichiers extraits au point `1.`, et `$OUTPUT_FOLDER` par le chemin vers le dossier dans lequel générer les CSV formatés, à savoir le dossier `db/seeds` du depôt `envinorma-web` cloné au point `2.`)

Cette opération va notamment uploader la liste des APs à OCRiser sur OVH.

## 2. Exécuter l'OCR sur les nouveaux APs

Pour cela, utiliser la même librairie data-tasks et suivre ces [instructions](https://github.com/Envinorma/data-tasks#faire-tourner-locr-sur-les-aps-dont-locr-na-pas-%C3%A9t%C3%A9-ex%C3%A9cut%C3%A9).

Cette opération va utiliser la liste des APs générée précédemment et appliquer l'OCR à tous les APs n'ayant pas déjà été OCRisés.

## 3. Générer à nouveau `aps_*.csv`

Désormais, le statut OCR et la taille des AP peuvent être modifiés, on peut donc générer à nouveau le fichier `aps_*.csv` à partir des [mêmes instructions](https://github.com/Envinorma/data-tasks#mettre-%C3%A0-jour-les-fichiers-apscsv-%C3%A0-partir-de-lextraction-g%C3%A9orisques).

## 4. Seeder les APs dans l'application Envinorma

1. Maintenant que les fichiers `aps_*.csv` ont été générés dans le dossier `envinorma-web/db/seeds`, les commiter et les pusher
1. Déployer l'app (cf [https://github.com/Envinorma/envinorma-web/README.md](https://github.com/Envinorma/envinorma-web/README.md)), puis seeder les aps dans l'application Envinorma, en exécutant la commande suivante dans la console rails de production :

```ruby
DataManager.seed_aps
```
