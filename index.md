---
layout: page
title: Accueil
nav_order: 1
---

# Envinorma - documentation technique

Cette page rassemble la documentation technique et les archives du projet Envinorma. Une page d'introduction au projet est consultable [ici](https://entrepreneur-interet-general.etalab.gouv.fr/defis/2020/envinorma.html).

# Applications

## envinorma.herokuapp.com

Le code source est accessible [ici](https://github.com/Envinorma/envinorma-web) et les instructions pour lancer l'application en local et la déployer sur Heroku sont consultables [ici](<(https://github.com/Envinorma/envinorma-web/README.md)>).

## envinorma-back-office.herokuapp.com

Le back-office permet de manipuler les textes réglementaires. Les instructions de lancement sont consultables [ici](https://github.com/Envinorma/back-office#ex%C3%A9cuter-en-local) et les instructions de déploiement sont consultables [ici](https://github.com/Envinorma/back-office#7-d%C3%A9ployer-sur-heroku).

# Mise à jour des données

Les données dont dépend Envinorma sont décrites [ici](https://github.com/Envinorma/exploration/blob/main/data_sources.md).

1. [Mettre les installations et les classements à jour à partir de S3IC](/data_updates/update_classements.md)
2. [Mettre les APs à jour à partir des données géorisques](/data_updates/update_aps.md)
3. [Mettre la nomenclature à jour à partir des données géorisques](/data_updates/update_nomenclature.md)
4. [Mettre à jour les AM envinorma après une modification sur le back-office](/data_updates/update_ams.md)
5. [Comment mettre à jour un AM (métier)](/data_updates/edit_am.md)

# Architecture

- Architecture des services décrite [ici](/architecture/schema_fonctionnel.md).
- Architecture de envinorma-web
- Architecture de envinorma-data
- Architecture de data-tasks
- Architecture de back-office
- [Librairie de manipulation de l'API Legifrance](https://github.com/Envinorma/leginorma)

# Reco/futur (la dernière semaine)

- Connexion GUN
- Maintenance
- Prospectives
- Fonctionnalités

# Archives

- [Tableau des retours utilisateurs](https://github.com/orgs/Envinorma/projects/2?fullscreen=true)
- [Tableau de suivi des tâches](https://github.com/orgs/Envinorma/projects/1?fullscreen=true)
- Le support de Laure
- La vidéo pitch
- La vidéo de cloture
- Le MIRO
- Le FIGMA

# Outils divers

- google analytics
- Heroku prod
- Heroku staging
- sentry
- Hotjar
- Resana ?
