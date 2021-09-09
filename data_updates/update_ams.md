---
layout: default
title: Arrêtés ministériels
permalink: /data/am
parent: Mise à jour des données
nav_order: 3
---

# Mise à jour des arrêtés ministériels dans l'application Envinorma

Les AM sont édités via le back-office et doivent ensuite être exportés dans la base de donnée de l'application Envinorma. Ce document décrit la marche à suivre.

### 1. Générer le fichier zip contenant les AM de la base de donnée du back office

- Se rendre sur [cette page](https://envinorma-back-office.herokuapp.com/upload_ams) du back-office.
- Cliquer sur le bouton `Exporter`. L'opération peut prendre jusqu'à deux minutes. Si tout se passe bien, une alerte verte s'affiche indiquant le nom du fichier créé dans le [dépôt OVH contenant les AM](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/am).

Le fichier ainsi créé est un zip contenant autant de fichiers qu'il y a d'AM en vigueur dans la base de donnée du back-office. Chaque nom de fichier est de la forme `CID.json`, où CID est l'identifiant Légifrance du texte.

### 2. Mettre à jour les AM dans Envinorma

- Télécharger le zip ainsi créé, le dézipper et copier les fichiers AM dans le dossier `db/seeds/ams` du dépôt `envinorma-web`
- Ajouter une tâche after party `bundle exec rails generate after_party:task seed_ams`
- Dans le fichier créé, ajouter `DataManager.seed_ams` après le commentaire `# Put your task implementation HERE.`
- Commit, push, deploy
