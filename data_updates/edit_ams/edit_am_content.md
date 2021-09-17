---
title: Modifier le contenu
permalink: /data/edit_ams/edit_am_content
parent: Modifier les AMs
grand_parent: Mise à jour des données
nav_order: 4
---

# Recommandations

- Le niveau de titre est indiqué par le nombre de symboles `#` au début de la ligne.
- Le sommaire de droite est mis à jour dynamiquement et peut aider à détecter les erreurs de structurations
- Les tableaux doivent être écrits en HTML, un outil d'aide à la création d'un tableau est disponible [ici](https://developer.mozilla.org/fr/docs/Web/HTML/Element/table). Attention, le tableau doit être entièrement écrit sur une ligne, comme ceci : `<table><thead><tr><th colspan="2">Première ligne</th></tr></thead><tbody><tr><td>Cellule A</td><td>Cellule B</td></tr></tbody></table>`.
- Lorsque le contenu est modifié, les thèmes et le paramétrage qui avaient été associés aux différentes sections de l'arrêté sont ré-associés en utilisant la valeur des titres. Si un titre a changé, il se peut que les éléments associés soient perdus. Ceci est est indiqué avant de confirmer l'enregistrement de l'arrêté. Il est possible d'enregistrer mais il faut penser à réaffecter les éléments perdus si besoin.
- Il est possible de repartir de la version Légifrance ou AIDA. Pour cela, utiliser les boutons `Remplacer par la version Légifrance` ou `Remplacer par la version AIDA`
- Les titres ne sont pas sélectionnables dans envinorma. Une ligne de l'arrêté doit donc être définie comme un titre seulement si elle ne contient pas de contenu important. En particulier, voici deux recommandations pour l'utilisation des titres :

### 1. Pas de titres dans les énumérations

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

### 2. Pas de contenu prescriptif dans les titres

Dans certains cas, le titre est très long et contient en fait une prescription. Dans ce cas, il faut séparer le titre du contenu prescriptif, quitte à laisse la numérotation seule dans le titre.

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
