---
layout: default
title: Évolution et maintenance
permalink: /next_steps/maintenance
parent: Suite du projet
nav_order: 2
---

# Évolution et maintenance

## Évolution
### Récupération des données via l'API GUN

Aujourd'hui, on récupère des données à partir de [plusieurs sources](https://github.com/Envinorma/exploration/blob/main/data_sources.md), l'idéal serait de ne pouvoir dépendre que de l'API GUN. Il faut donc s'y connecter lorsqu'elle sera prête (prévu pour le 1er semestre 2022).

> ⚠️ il est important de suivre la mise en production pour s'assurer que toutes les données dont dépend Envinorma seront présentes dans cette API unique. (cf: [liste des données utilisées par Envinorma](https://github.com/Envinorma/exploration/blob/main/data_sources.md))

## Maintenance
### Outil maintenance

- Sur [Heroku](https://dashboard.heroku.com/apps/envinorma/) il existe un mode maintenance pour afficher la page "Maintenance" en cas d'indisponibilité du site. Cliquer sur l'onglet `Settings` et activer le mode maintenance.
- Les bugs sont monitorés par l'outil Sentry à travers un add-on sur l'hébergement [Heroku](https://dashboard.heroku.com/apps/envinorma/).


### Maintenance technique
- Correction de bugs mineurs (envinorma et envinorma-back-office)
- Mise à jour des dépendances (notamment celle indiquées par le dependabot sur Github - envinorma-web)
- Mise à jour manuelle des données pour les AMs et pour les Installations. (Voir [Mise à jour des données](/data))

### Rôle du porteur de projet
- Mettre envinorma en mode maintenance en cas de bug
- Consulter et gérer les notifications de bugs, les mails utilisateurs sur l’adresse générique
- Notifier les mainteneurs de l’application à réception des dumps S3IC et géorisques (et en cas de bug)
- Suivre l'évolution des AM et les mettre à jour via le back-office
- Alimenter la FAQ en fonction des retours utilisateurs ou d'une évolution de service (la partie technique est à faire par un.e développeur.se)

#### Autres tâches :
- Suivre l’avancée des projets connexes (GUN, notamment pour l’API)
- Assurer la communication et prévoir d’éventuels développements, pilotages futurs
