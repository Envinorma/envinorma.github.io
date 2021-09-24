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

Cliquer sur le bouton `Exporter les AMs` depuis la page d'accueil du [back-office](https://envinorma-back-office.herokuapp.com).

L'opération peut prendre jusqu'à deux minutes. Si tout se passe bien, une alerte verte s'affiche indiquant le nom du fichier créé dans le [dépôt OVH contenant les AM](https://storage.sbg.cloud.ovh.net/v1/AUTH_3287ea227a904f04ad4e8bceb0776108/am). Cette opération écrase également le fichier `ams/latest.zip` dans ce dépôt OVH.

Le fichier ainsi créé est un zip contenant autant de fichiers qu'il y a d'AM en vigueur dans la base de données du back-office. Chaque nom de fichier est de la forme `CID.json`, où CID est l'identifiant Légifrance du texte.

### Import des AMs et mise à jour dans Envinorma

Exécuter la commande suivante Dans la console Rails de production (soit depuis le terminal, soit depuis l'interface d'Heroku) :

```ruby
DataManager.seed_ams(from_ovh: true)
```

**NB**

- Pour ouvrir la console depuis Heroku, ouvrir l'application depuis le dashboard Heroku puis cliquer sur `More`, `Run console`, écrire `console` dans la popup qui s'ouvre, puis cliquer sur `Run`
- Cette commande télécharge le fichier `ams/latest.zip`, le décompresse dans `db/seeds/ams`, valide les nouveaux AM et met à jour la base.
- Il est possible de commiter les fichiers AMs ainsi crées pour permettre la tracabilité des modifications.

Et voilà 🎉
