---
layout: default
title: Architecture des services
permalink: /architecture/schema_fonctionnel
parent: Architecture
nav_order: 1
---

# Architecture technique du projet Envinorma

Il y a quatre composants principaux au projet :

- L'[application principale](https://envinorma.herokuapp.com) (et son double de [pré-prod](https://envinorma-staging-1.herokuapp.com))
- Un [back office](https://envinorma-back-office.herokuapp.com)
- Un workflow de tâches de préparation des données, implémentées [ici](https://github.com/Envinorma/data-tasks) et exécutées avec [Prefect](https://www.prefect.io/)
- Deux buckets de stockages d'objets, pour stocker les [AP transformés](http://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/ap/) et les [AM transformés](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/am/)

## Liste des applications

![image](https://user-images.githubusercontent.com/11191435/128323537-def749ce-c256-4193-bcba-91a6b8cfea65.png)

#### Liste des tâches référencées sur le schéma ci-dessus

1.  Ecriture des données ICPE (AP, installations et classements) dans la bdd Envinorma à partir de fichiers fournis par la DGPR et le BRGM _(2 minutes d’exécution, 1 fois par semaine)_
2.  Détection des nouvelles versions d’AM publiées à partir de l’API Legifrance et du site aida.ineris.fr. Notification slack. _(10 min d’exécution, 1 fois par semaine)_
3.  OCR des nouveaux AP à partir de la bdd Envinorma et des AP déjà uploadés dans le bucket _(3h d’exécution, 1 fois par semaine)_
4.  Reconstruction des AM de la base de données Envinorma à partir de la base de données Back-office _(5 min d’exécution, 1 fois par semaine ou à la demande)_
5.  Construction du fichier des AM à partir de la base de données back-office (upload dans un bucket OVH) _(5 min d'exécution, 1 fois par semaine)_

### App envinorma

- Actuellement déployée sur Heroku, version payante pour la base de donnée et la dyno
- Postgres v12.7, 400k lignes, 10 tables, 125 Mo de données, backup hebdomadaire
- App : ruby 2.7.4, rails 6.0.4.
  - Toutes les dépendances ruby : https://github.com/Envinorma/envinorma-web/blob/master/Gemfile
  - Toutes les dépendances javascript : https://github.com/Envinorma/envinorma-web/blob/master/yarn.lock
  - RAM: 512 Mo
  - 1 CPU
  - Espace disque: 500Mo
  - Pas d'authentification
  - https

### App envinorma-staging (environnement de pre-prod)

- Actuellement déployée sur Heroku, version gratuite
- Mêmes caractéristiques qu'Envinorma, avec une base de données plus petite

### App back-office

- Actuellement déployée sur Heroku, version gratuite
- Postgres v12.7, 2000 lignes, 5 tables, 33Mo de données, backup hebdomadaire
- App : python 3.9, dash 1.21.0
  - Liste des dépendances : [https://github.com/Envinorma/back-office/blob/main/requirements.txt](https://github.com/Envinorma/back-office/blob/main/requirements.txt)
  - RAM: 512 Mo
  - 1 CPU
  - Espace disque: 500Mo
  - Authentification simple
  - https

### Data-tasks (tâches effectuées périodiquement pour préparer la donnée nécessaire au bon fonctionnement des applications)

- Docker, Python 3.9, prefect v0.14.19 pour la gestion du workflow
- Liste des dépendances python : https://github.com/Envinorma/data-tasks/blob/main/requirements.txt
- Package ubuntu dépendants pour l’OCR : ghostscript, icc-profiles-free, liblept5, libxml2, pngquant, python3-pip, tesseract-ocr, tesseract-ocr-fra, zlib1g

### Stockage d’objets

- Deux buckets : un pour les AM et un pour les AP.
- Capacité de l'ordre de 150Go en tout
- Accessible via https, exemple : https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/ap/P/6/9107c345c15a46e681e2a5546dca78d6.pdf

### Monitoring

- Sentry pour l’app envinorma
- Google analytics pour l’app envinorma
- Slack pour les data-tasks et le back-office
- Prefect pour le monitoring des data-tasks
- Heroku dashboard pour le monitoring des utilisations en RAM/CPU/Disque des deux applications et bases de données
