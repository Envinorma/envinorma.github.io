---
layout: default
title: Nomenclature
permalink: /data/nomenclature
parent: Mise à jour des données
nav_order: 4
---

# Mise à jour des références de classements (nomenclature)

Pour effectuer une mise à jour sur la nomenclature, il faut :

1. Cloner le dépôt [https://github.com/Envinorma/envinorma-web](https://github.com/Envinorma/envinorma-web)
2. Modifier manuellement le fichier `db/seeds/classement_references.csv` selon les modifications souhaitées de la nomenclature
3. _Commit_ et _push_ le fichier `db/seeds/classement_references.csv`
4. Déployer l'app (cf [https://github.com/Envinorma/envinorma-web/README.md](https://github.com/Envinorma/envinorma-web/README.md)) puis mettre à jour ces références dans l'application Envinorma, en exécutant la commande suivante dans la console rails :
   ```ruby
   DataManager.seed_classement_references
   ```
