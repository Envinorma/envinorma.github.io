---
layout: default
title: Arrêtés préfectoraux
permalink: /data/ap
parent: Mise à jour des données
nav_order: 2
---

# Mise à jour des arrêtés préfectoraux

Les APs sont mis à jour automatiquement et quotidiennement à partir des extractions Géorisques. Un script python exécute l'OCR sur les APs à `7am UTC` et une tâche rake met à jour les APs de l'application de production à `9pm UTC`.


## Prérequis (si besoin de lancer les scripts manuellement)

_Pour exécuter les scripts, les identifiants OVH, slack et Heroku sont nécessaires. Ils peuvent être récupérés via Resana sur demande à un responsable du projet._

## Mise à jour de la liste des APs et OCR des APs

Un script python est exécuté quotidiennement via une tâche CRON de l'utilisateur `root` de la [machine OVH](https://www.ovh.com/manager/public-cloud/#/pci/projects/3287ea227a904f04ad4e8bceb0776108/instances/1ac362a1-09cd-445b-a90a-def7dcaeaaff) `data-tasks`.
- il télécharge le dump géorisques du matin
- il génère les fichiers `aps_all.csv`, `aps_idf.csv` et `aps_sample.csv` dans le [bucket OVH](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/misc) associé
- il exécute l'OCR sur les nouveaux APs
- il met à jour le statut OCR des APs dans les fichiers `aps_all.csv`, `aps_idf.csv` et `aps_sample.csv`.

Ce script est contenu dans le fichier `scripts/update_ap.sh` du dépôt [data-tasks](https://github.com/Envinorma/data-tasks).


### Pour l'exécuter manuellement ou dans un nouvel environnement :

1. Cloner le dépôt [data-tasks](https://github.com/Envinorma/data-tasks) en local

   ```sh
   git clone https://github.com/Envinorma/data-tasks
   ```

2. Avoir installé [docker](https://docs.docker.com/get-docker/)
3. Construire l'image docker

   ```sh
   cd data-tasks
   docker build -t tasks .
   ```

4. Exécuter le script (après avoir remplacé les 6 occurrences de `REPLACE_ME` par la valeur du secret associé.)
   ```sh
   docker run -it --rm\
     -e OVH_OS_TENANT_ID=REPLACE_ME\
     -e OVH_OS_TENANT_NAME=REPLACE_ME\
     -e OVH_OS_USERNAME=REPLACE_ME\
     -e OVH_OS_PASSWORD=REPLACE_ME\
     -e SLACK_AM_CHANNEL=REPLACE_ME\
     -e GEORISQUES_DATA_URL=REPLACE_ME\
     tasks\
     sh scripts/update_aps.sh
   ```

## Mise à jour des APs dans l'application de production

Une tâche rake `lib/tasks/update_aps.rake` (dans l'application Envinorma) est exécutée pour mettre à jour les APs. Elle est programmée à 9pm UTC tous les jours via le [Heroku Scheduler](https://dashboard.heroku.com/apps/envinorma/scheduler). Celle-ci exécute la tâche suivante, qui télécharge le fichier [aps_all.csv](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/misc/aps_all.csv) de ce bucket OVH puis met à jour les APs en base de donnée.

```ruby
DataManager.seed_aps(from_ovh: true)
```
