---
layout: default
title: Évolution et maintenance
permalink: /next_steps/maintenance
parent: Suite du projet
nav_order: 2
---

# Évolution et maintenance

## Récupération des données via l'API GUN

Aujourd'hui, on récupère des données à partir de [plusieurs sources](https://github.com/Envinorma/exploration/blob/main/data_sources.md), l'idéal serait de ne pouvoir dépendre que de l'API GUN. Il faut donc s'y connecter lorsqu'elle sera prête (prévu pour le 1er semestre 2022).

> ⚠️ il est important de suivre la mise en production pour s'assurer que toutes les données dont dépend Envinorma seront présentes dans cette API unique. (cf: [liste des données utilisées par Envinorma](https://github.com/Envinorma/exploration/blob/main/data_sources.md))

## Maintenance

- Sur [Heroku](https://dashboard.heroku.com/apps/envinorma/) il existe un mode maintenance pour afficher la page "Maintenance" en cas d'indisponibilité du site. Cliquer sur l'onglet `Settings` et activer le mode maintenance.
- Les bugs sont monitorés par l'outil Sentry à travers un add-on sur l'hébergement [Heroku](https://dashboard.heroku.com/apps/envinorma/).
