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

- [Architecture des services](/architecture/schema_fonctionnel.md).
- Architecture de envinorma-web
- [Architecture de envinorma-data](https://envinorma.github.io/envinorma-data/#modules-principaux)
- [Architecture de data-tasks](https://github.com/Envinorma/data-tasks#data-tasks)
- [Architecture du dépôt back-office](https://github.com/Envinorma/back-office#structure)
- [Librairie de manipulation de l'API Legifrance](https://github.com/Envinorma/leginorma)

# Reco/futur (la dernière semaine)

- Connexion GUN
- Maintenance
- Prospectives
- Fonctionnalités

# Archives

- [Tableau des retours utilisateurs](https://github.com/orgs/Envinorma/projects/2?fullscreen=true)
- [Tableau de suivi des tâches](https://github.com/orgs/Envinorma/projects/1?fullscreen=true)
- [La présentation de restitution de la phase design](https://resana.numerique.gouv.fr/public/document/consulter/1429124?slug=16981)
- [Vidéo dans le cadre de la fin du programme EIG](https://www.youtube.com/watch?v=JMa3h5d-X0A&t=1s)
- [Vidéo d'introduction de l'outil](https://www.loom.com/share/41d0e1bc23bb489495a58b323fae0348?t=0)
- Le MIRO
- Le FIGMA

# Outils divers

- google analytics
- [Heroku prod](https://dashboard.heroku.com/apps/envinorma)
- [Heroku staging](https://dashboard.heroku.com/apps/envinorma-staging-1)
- [Heroku back-office](https://dashboard.heroku.com/apps/envinorma-back-office)
- Heroku staging
- Sentry via Heroku
- Hotjar
- [Slack](https://envinorma.slack.com)
- [Resana](https://resana.numerique.gouv.fr/public/perimetre/consulter/16981) (accès via un animateur du projet)
