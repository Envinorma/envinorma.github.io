---
layout: default
title: Installations et classements
permalink: /data/classements
parent: Mise à jour des données
nav_order: 1
---

# Mise à jour des installations et des classements

Les classements sont mis à jour manuellement à partir des extractions S3IC. Il faut éxécuter un script pour générer des fichiers CSV bien formattés puis les mettre à jour sur Envinorma-web.

## Prérequis

_Pour exécuter les scripts, les identifiants OVH et Heroku sont nécessaires. Ils peuvent être récupérés via Resana sur demande à un responsable du projet._

1. avoir les deux fichiers issus de l'extraction DGPR: `s3ic-liste-etablissements.csv` et `sic-liste-rubriques.csv` dans un dossier en local (un dump est disponible sur Resana).

1. avoir le dépôt [data-tasks](https://github.com/Envinorma/data-tasks) en local

   ```sh
   git clone https://github.com/Envinorma/data-tasks
   ```
1. avoir le dépôt [Envinorma-web](https://github.com/Envinorma/envinorma-web) en local

   ```sh
   git clone https://github.com/Envinorma/envinorma-web
   ```

## Générer les nouveaux CSV

Le script va créer de nouveaux CSV dans OVH (`installations_all.csv`, `installations_idf.csv`, `installations_sample.csv`, `classements_all.csv`, `classements_idf.csv`, `classements_sample.csv`) à partir des deux CSV extraits d'S3IC `s3ic-liste-etablissements.csv` et `sic-liste-rubriques.csv`

### Éxécuter le script

Se placer dans le dossier data-tasks

```sh
cd data-tasks
```

Remplacer `$INPUT_FOLDER` par le chemin vers le dossier contenant les deux fichiers issus de l'extraction S3IC et les 4 occurrences de `REPLACE_ME` par la valeur du secret associé.

> ex : `$INPUT_FOLDER` -> `/Users/lisadurand/Downloads/210909_Envinorma`

```sh
docker build -t tasks .
docker run -it --rm\
  -v $INPUT_FOLDER:/data/secret_data\
  -e OVH_OS_TENANT_ID=REPLACE_ME\
  -e OVH_OS_TENANT_NAME=REPLACE_ME\
  -e OVH_OS_USERNAME=REPLACE_ME\
  -e OVH_OS_PASSWORD=REPLACE_ME\
  tasks\
  python3 -m tasks.data_build.generate_data --handle-installations-data
```

## Mettre en ligne

### Se placer dans le dossier envinorma-web

```sh
cd envinorma-web
```

### Télécharger les fichiers créés

Depuis le bucket OVH, télécharger les fichiers [installations_all.csv](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/misc/installations_all.csv) et [classements_all.csv](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/misc/classements_all.csv) et les placer dans le dossier `envinorma-web/db/seeds`.

### _Commit_ et _push_

```sh
git add .
git commit -m "MAJ des installations et classements"
git push heroku master
```

Pour en savoir plus pour [pusher sur Heroku](https://github.com/Envinorma/envinorma-web/#d%C3%A9ployer-sur-heroku)

## Mettre à jour les données en production

Exécuter la commande suivante dans la console Rails de production (depuis le terminal ou depuis l'interface d'Heroku)

```ruby
DataManager.seed_installations_and_associations
```

Et voilà 🎉
