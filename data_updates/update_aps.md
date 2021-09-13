---
layout: default
title: Arrêtés préfectoraux
permalink: /data/ap
parent: Mise à jour des données
nav_order: 2
---

# Mise à jour des arrêtés préfectoraux

Les APs sont mis à jour à partir des extractions Géorisques.
La liste des AP est mise à jour et seedée dans envinorma-web. Les AP sont OCRisés et stockés sur OVH.


## Prérequis :

_Pour exécuter les scripts, les identifiants OVH et Heroku sont nécessaires. Ils peuvent être récupérés via Resana sur demande à un responsable du projet._

1. avoir les deux fichiers issus de l'extraction Géorisques: `IC_documents.csv` et `IC_types_document.csv` dans un dossier en local

2. avoir le dépôt [Envinorma-web](https://github.com/Envinorma/envinorma-web) en local
  ```
    git clone git@github.com:Envinorma/envinorma-web.git
  ```
1. avoir le dépôt [Data-tasks](https://github.com/Envinorma/data-tasks) en local
  ```
  git clone https://github.com/Envinorma/data-tasks
  ```
1. avoir mis à jour les [installations](http://localhost:4000/data/classements)
1. avoir installé [docker](https://docs.docker.com/get-docker/)



## MAJ de la liste des AP à OCRiser

Le script va créer de nouveaux CSV (`aps_all.csv`, `aps_idf.csv`, `aps_sample.csv`) à partir des deux CSV extraits de Géorisques `IC_documents.csv` et `IC_types_document.csv`.
> _Pour l'instant on ne va pas utiliser ces fichiers._

Le script uploade également une liste à jour avec les ID des APs sur OVH.

### Éxécuter le script

Se placer dans le dossier data-tasks
```
cd data-tasks
```

Remplacer `$INPUT_FOLDER` par le chemin vers le dossier contenant les deux fichiers issus de l'extraction Géorisques et `$OUTPUT_FOLDER` par le chemin vers le dossier des seeds dans le dossier envinorma-web où vont être générés les 3 nouveaux fichiers.
/!\ le dossier d'output doit contenir les fichiers `installations_all.csv`, `installations_idf.csv`, `installations_sample.csv`.

> ex : `$INPUT_FOLDER` -> `/Users/lisadurand/Downloads/s3ic/S3IC-Georisques`\
> ex : `$OUTPUT_FOLDER` -> `/Users/lisadurand/code/envinorma-web/db/seeds`

Remplacer les 4 occurrences de `REPLACE_ME` par les identifiants OVH

#### Avec Docker
```
docker build -t tasks .
docker run -it --rm\
  -v $INPUT_FOLDER:/data/georisques\
  -v $OUTPUT_FOLDER:/data/seeds\
  -e OVH_OS_TENANT_ID=REPLACE_ME\
  -e OVH_OS_TENANT_NAME=REPLACE_ME\
  -e OVH_OS_USERNAME=REPLACE_ME\
  -e OVH_OS_PASSWORD=REPLACE_ME\
  tasks\
  python3 -m tasks.data_build.generate_data --handle-aps
```

#### Avec python >= 3.8
```
cp default_config.ini config.ini
# Modifier config.ini pour définir storage.seed_folder=$OUTPUT_FOLDER et storage.georisques_data_folder=$INPUT_FOLDER
# Modifier aussi les valeurs de OS_TENANT_ID, OS_TENANT_NAME, OS_USERNAME, OS_PASSWORD avec les identifiants OVH
virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
python3 -m tasks.data_build.generate_data --handle-aps
```


## Exécuter l'OCR sur les nouveaux APs et les uploader sur OVH
À partir de la liste des ID uploadée dans le script précédent sur OVH, le script va appliquer l’OCR à tous les APs n’ayant pas déjà été OCRisés, puis les uploader sur OVH.

Remplacer les 4 occurrences de `REPLACE_ME` par les identifiants OVH

#### Avec Docker
```
docker build -t ocr -f ocr.dockerfile .
docker run -it --rm\
  -e OS_AUTH_URL="https://auth.cloud.ovh.net/v3/"\
  -e OS_IDENTITY_API_VERSION=3\
  -e OS_USER_DOMAIN_NAME=Default\
  -e OS_PROJECT_DOMAIN_NAME=Default\
  -e OS_TENANT_ID=REPLACE_ME\
  -e OS_TENANT_NAME=REPLACE_ME\
  -e OS_USERNAME=REPLACE_ME\
  -e OS_PASSWORD=REPLACE_ME\
  -e OS_REGION_NAME=SBG\
  ocr
```


## Générer les fichiers CSV
Après l'étape d'OCRisation, les 3 fichiers `aps_*.csv` ont besoin d'être mis à jour car le poids et le statut de l'OCR (ex: success) ont changé.
On va donc rejouer le script pour regénérer les 3 fichiers : `aps_all.csv`, `aps_idf.csv`, `aps_sample.csv` que l'on va cette fois-ci utilisé pour seeder envinorma-web.


## Mettre en ligne

### Se placer dans le dossier envinorma-web
```
cd ../envinorma-web
```

### Commiter et pusher
Le script précédent a ajouté 3 nouveaux CSV dans le dossier `db/seeds` d'envinorma-web.
Il faut maintenant les ajouter au repo distant sur Heroku.

```
git add .
git commit -m "MAJ des installations et classements"
git push heroku master
```
Pour en savoir plus pour [pusher sur Heroku](https://github.com/Envinorma/envinorma-web/#d%C3%A9ployer-sur-heroku)


## Mettre à jour les données en production

Exécuter la commande suivante Dans la console Rails de production (soit depuis le terminal, soit depuis  l'interface d'Heroku)
```
DataManager.seed_aps
```

Et voilà 🎉
