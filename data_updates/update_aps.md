---
layout: default
title: Arrêtés préfectoraux
permalink: /data/ap
parent: Mise à jour des données
nav_order: 2
---

# Mise à jour des arrêtés préfectoraux à partir de l'extraction Géorisques

_Pour exécuter les scripts, les identifiants OVH et Heroku sont nécessaires. Ils peuvent être récupérés via Resana sur demande à un responsable du projet._

## 1. Générer aps_all.csv

Pour cela, utiliser la librairie data-tasks et suivre ces [instructions](https://github.com/Envinorma/data-tasks#mettre-%C3%A0-jour-les-fichiers-apscsv-%C3%A0-partir-de-lextraction-g%C3%A9orisques) pour générer le fichier `aps_all.csv` dans `envinorma-web/db/seeds`.

## 2. Exécuter l'OCR sur les nouveaux APs

Pour cela, utiliser la même librairie et suivre ces [instructions](https://github.com/Envinorma/data-tasks#faire-tourner-locr-sur-les-aps-dont-locr-na-pas-%C3%A9t%C3%A9-ex%C3%A9cut%C3%A9).

## 3. Générer à nouveau aps_all.csv

Désormais, le statut OCR et la taille des AP peuvent être modifiés, on peut donc générer à nouveau le fichier aps_all.csv à partir des [mêmes instructions](https://github.com/Envinorma/data-tasks#mettre-%C3%A0-jour-les-fichiers-apscsv-%C3%A0-partir-de-lextraction-g%C3%A9orisques).

## 4. Seeder les APs dans l'application Envinorma

Exécuter la commande suivante dans la console rails :

```ruby
DataManager.seed_aps
```
