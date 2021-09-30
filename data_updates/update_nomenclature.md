---
layout: default
title: Nomenclature
permalink: /data/nomenclature
parent: Mise à jour des données
nav_order: 4
---

# Mise à jour des références de classements (nomenclature)

Pour effectuer une mise à jour sur la nomenclature, il faut :

1. avoir le dépôt [Envinorma-web](https://github.com/Envinorma/envinorma-web) en local

   ```sh
   git clone https://github.com/Envinorma/envinorma-web
   ```
2. modifier manuellement le fichier `db/seeds/classement_references.csv` selon les modifications souhaitées de la nomenclature
3. _commit_ et _push_ le fichier `db/seeds/classement_references.csv`
  ```sh
  git add .
  git commit -m "MAJ de la nomenclature"
  git push heroku master
  ```
  Pour en savoir plus pour [pusher sur Heroku](https://github.com/Envinorma/envinorma-web/#d%C3%A9ployer-sur-heroku)

4. mettre à jour les données en production en exécutant la commande suivante dans la console Rails de production (depuis le terminal ou depuis l'interface d'Heroku)

```ruby
DataManager.seed_classement_references
```

Et voilà 🎉
