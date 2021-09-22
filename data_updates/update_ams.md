---
layout: default
title: Arrêtés ministériels
permalink: /data/am
parent: Mise à jour des données
nav_order: 3
---

# Mise à jour des arrêtés ministériels dans l'application Envinorma

Les AM sont édités via le [back-office](https://envinorma-back-office.herokuapp.com/) et doivent ensuite être exportés sur OVH puis importés dans la base de données de l'application Envinorma.

### Export des AMs depuis le back-office

Cliquer sur le bouton `Exporter` depuis la page d'accueil du [back-office](https://envinorma-back-office.herokuapp.com).

L'opération peut prendre jusqu'à deux minutes. Si tout se passe bien, une alerte verte s'affiche indiquant le nom du fichier créé dans le [dépôt OVH contenant les AM](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/am).

Le fichier ainsi créé est un zip contenant autant de fichiers qu'il y a d'AM en vigueur dans la base de données du back-office. Chaque nom de fichier est de la forme `CID.json`, où CID est l'identifiant Légifrance du texte.


### Import des AMs et mise à jour dans Envinorma
#### Ajouter les fichiers dans le dépôt Envinorma
Télécharger le zip ainsi créé, le dézipper et copier les fichiers AM dans le dossier `db/seeds/ams` du dépôt `envinorma-web`

#### Committer et mettre en production
```
git add .
git commit -m "Import des nouveaux Ams"
git push heroku master
```
Pour en savoir plus pour [pusher sur Heroku](https://github.com/Envinorma/envinorma-web/#d%C3%A9ployer-sur-heroku)

#### Mettre à jour les données en production

Exécuter la commande suivante Dans la console Rails de production (soit depuis le terminal, soit depuis  l'interface d'Heroku)
```
DataManager.seed_ams
```

Et voilà 🎉
