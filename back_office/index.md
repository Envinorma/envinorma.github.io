---
layout: page
title: Back office
permalink: /back_office
has_children: true
nav_order: 4
---

# Back office

Les AM sont édités via le [back-office](https://envinorma-back-office.herokuapp.com/) et doivent ensuite être exportés sur OVH puis importés dans la base de données de l'application Envinorma.

## Prérequis

_Pour manipuler les AMs, il faut avoir les login du Back-office._

## Manipulation des AMs

Via le back-office on peut modifier, abroger ou créer de nouveaux AMs.
La création/modification est divisée en 4 étapes clés :

- les renseignements généraux (les metadonnées)
- le contenu ([voir éditer le contenu](/back_office/edit_content))
- le paramétrage ([voir éditer le paramétrage](/back_office/edit_parameters))
- les thèmes

## Export des AMs et intégration à Envinorma

La communication entre le back-office et l'application web Envinorma n'est pas automatisée. Une fois que les AMs sont prêts, il faut les exporter dans OVH depuis la page d'accueil du back-office, puis les intégrer à Envinorma. [Voir la marche à suivre](/data/am)
