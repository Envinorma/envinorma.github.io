---
layout: default
title: Installations et classements
permalink: /data/classements
parent: Mise à jour des données
nav_order: 1
---

# Mise à jour des installations et des classements

Les classements sont mis à jour à partir des extractions S3IC. Il faut éxécuter un script pour générer des fichiers CSV bien formattés puis les mettre à jour sur Envinorma-web.

## Prérequis

_Pour exécuter les scripts, les identifiants OVH et Heroku sont nécessaires. Ils peuvent être récupérés via Resana sur demande à un responsable du projet._

1. avoir les deux fichiers issus de l'extraction DGPR: `s3ic-liste-etablissements.csv` et `sic-liste-rubriques.csv` dans un dossier en local

2. avoir le dépôt [Envinorma-web](https://github.com/Envinorma/envinorma-web) en local

```sh
git clone git@github.com:Envinorma/envinorma-web.git
```

1. avoir le dépôt [Data-tasks](https://github.com/Envinorma/data-tasks) en local

```sh
git clone https://github.com/Envinorma/data-tasks
```

## Générer les nouveaux CSV

Le script va créer de nouveaux CSV (`installations_all.csv`, `installations_idf.csv`, `installations_sample.csv`, `classements_all.csv`, `classements_idf.csv`, `classements_sample.csv`) à partir des deux CSV extraits d'S3IC `s3ic-liste-etablissements.csv` et `sic-liste-rubriques.csv`

### Éxécuter le script

Se placer dans le dossier data-tasks

```
cd data-tasks
```

Remplacer `$INPUT_FOLDER` par le chemin vers le dossier contenant les deux fichiers issus de l'extraction S3IC et `$OUTPUT_FOLDER` par le chemin vers le dossier des seeds dans le dossier envinorma-web où vont être générés les 5 nouveaux fichiers.

> ex : `$INPUT_FOLDER` -> `/Users/lisadurand/Downloads/210909_Envinorma`\
> ex : `$OUTPUT_FOLDER` -> `/Users/lisadurand/code/envinorma-web/db/seeds`

#### Avec Docker

```sh
docker build -t tasks .
docker run -it --rm\
  -v $INPUT_FOLDER:/data/secret_data\
  -v $OUTPUT_FOLDER:/data/seeds\
  tasks\
  python3 -m tasks.data_build.generate_data --handle-installations-data
```

#### Avec python >= 3.8

```sh
cp default_config.ini config.ini
# Modifier config.ini pour définir storage.seed_folder=$OUTPUT_FOLDER et storage.secret_data_folder=$INPUT_FOLDER
virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
python3 -m tasks.data_build.generate_data --handle-installations-data
```

## Mettre en ligne

### Se placer dans le dossier envinorma-web

```sh
cd ../envinorma-web
```

### Commiter et pusher

Le script précédent a ajouté 5 nouveaux CSV dans le dossier `db/seeds` d'envinorma-web.
Il faut maintenant les ajouter au repo distant sur Heroku.

```sh
git add .
git commit -m "MAJ des installations et classements"
git push heroku master
```

Pour en savoir plus pour [pusher sur Heroku](https://github.com/Envinorma/envinorma-web/#d%C3%A9ployer-sur-heroku)

## Mettre à jour les données en production

Exécuter la commande suivante Dans la console Rails de production (soit depuis le terminal, soit depuis l'interface d'Heroku)

```ruby
DataManager.seed_installations_and_associations
```

Et voilà 🎉
