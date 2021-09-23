---
layout: default
title: Éditer le contenu
permalink: /back_office/edit_content
parent: Back office
nav_order: 1
---

# Éditer le contenu

À cette étape, on prépare et on structure le contenu. L'objectif premier est de corriger les erreurs de structuration pour que l'AM soit bien affiché du côté d'Envinorma.

## Fonctionnement global

Le langage de balisage utilisé est le markdown, le niveau de titre est indiqué par le nombre de symboles `#` au début de la ligne.

- `#` correspond à un titre de niveau 1
- `##` correspond à un titre de niveau 2

Le sommaire de droite est mis à jour dynamiquement et peut aider à détecter les erreurs de structuration.

_Le contenu peut-être rempli à partir de la version Légifrance ou Aida._

## Particularités

### Ajouter des tableaux

Les tableaux doivent être écrits en HTML, un outil d'aide à la création d'un tableau est disponible [ici](https://developer.mozilla.org/fr/docs/Web/HTML/Element/table). Attention, le tableau doit être entièrement écrit sur une ligne, comme ceci : `<table><thead><tr><th colspan="2">Première ligne</th></tr></thead><tbody><tr><td>Cellule A</td><td>Cellule B</td></tr></tbody></table>`.

### Modification avec thème et/ou paramétrage

Lorsque le contenu est modifié, les thèmes et le paramétrage qui avaient été associés aux différentes sections de l'arrêté sont ré-associés en utilisant la valeur des titres. Si un titre a changé, il se peut que les éléments associés soient perdus. Ceci est indiqué avant de confirmer l'enregistrement de l'arrêté. Il est possible d'enregistrer mais il faut penser à réaffecter les éléments perdus si besoin.

## Recommandations pour la structuration

Les titres ne sont pas sélectionnables dans envinorma. Une ligne de l'arrêté doit donc être définie comme un titre seulement si elle ne contient pas de contenu important. Voici deux exemples :

### Pas de titres dans les énumérations

Ok ✅

```markdown
# Article 1 - Lutte contre l'incendie

Il doit y avoir:
a) un extincteur
b) des portes coupe-feu
Il doit aussi y avoir une réserve d'eau
```

Pas ok 🚫

```markdown
# Article 1 - Lutte contre l'incendie

Il doit y avoir:

## a) un extincteur

## b) des portes coupe-feu

Il doit aussi y avoir une réserve d'eau
```

### Pas de contenu prescriptif dans les titres

Dans certains cas, le titre est très long et contient en fait une prescription. Dans ce cas, il faut séparer le titre du contenu prescriptif, quitte à laisser la numérotation seule dans le titre.

Ok ✅

```markdown
# Article 7

## 7-1.

Les locaux abritant un stockage de liquides inflammables présentent les caractéristiques de réaction et de résistance au feu minimales suivantes :[..]
Les commandes d'ouverture manuelle sont placées à proximité des accès aux locaux de stockage. Le système de désenfumage est adapté aux risques particuliers de l'installation.

## 7-2.

Les parties des bâtiments entre murs séparatifs où sont stockés des liquides inflammables ont une surface maximale égale à 1 500 mètres carrés en l'absence de système d'extinction automatique d'incendie et 3 000 mètres carrés en présence d'un système d'extinction automatique d'incendie spécifiquement adapté aux liquides inflammables et dimensionné pour permettre une extinction totale de l'incendie de la cellule concernée dans un délai maximum de trois heures.
```

Pas ok 🚫

```markdown
# Article 7

## 7-1. Les locaux abritant un stockage de liquides inflammables présentent les caractéristiques de réaction et de résistance au feu minimales suivantes :[..]

Les commandes d'ouverture manuelle sont placées à proximité des accès aux locaux de stockage. Le système de désenfumage est adapté aux risques particuliers de l'installation.

## 7-2. Les parties des bâtiments entre murs séparatifs où sont stockés des liquides inflammables ont une surface maximale égale à 1 500 mètres carrés en l'absence de système d'extinction automatique d'incendie et 3 000 mètres carrés en présence d'un système d'extinction automatique d'incendie spécifiquement adapté aux liquides inflammables et dimensionné pour permettre une extinction totale de l'incendie de la cellule concernée dans un délai maximum de trois heures.
```

Dans un cas complexe comme celui-ci, si l'article n'est pas trop long, ne pas hésiter à enlever tous les titres (en retirant les "#") pour éviter la confusion.
