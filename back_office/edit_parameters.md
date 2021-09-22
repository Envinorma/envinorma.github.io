---
title: Editer le paramétrage
permalink: /back_office/edit_parameters
parent: Back office
nav_order: 2
---

# Éditer le paramétrage de l'arrêté
À cette étape, on "paramètre" l'AM. On peut ajouter des conditions d'innaplicabilité ou des avertissements afin d'afficher une version "personnalisé" de l'AM côté Envinorma.

Plusieurs cas de figure :

- `Section non applicable` : un paragraphe (ou certains alinéas d'un paragraphe) ne s'applique pas dans certaines conditions\
  _ex: un AM peut être inapplicable lorsque la date de mise en service de l'installation est antérieure à une certaine date._
- `Section modification` : un paragraphe peut être modifié dans certaines conditions
- `Avertissement` : un paragraphe peut être accompagné d'un avertissement (lorsque les deux cas précédents ne suffisent pas)\
  _ex: on peut vouloir signaler qu'un AM n'est pas applicable si l'exploitant n'en a pas fait la demande._


## Recommandations pour le paramétrage

### ⚠️ Ne pas sur-paramétrer

Lorsque la condition est assez évidente et précisée dans le paragraphe concerné, il est inutile de la renseigner. Il est intéressant de renseigner une modification/non-application si son absence entrave la lecture ou peut être source d'erreur.

### ⚠️ Veillez aux incompatibilités

Lorsque plusieurs paramètres sont attachés à la même section, il faut veiller à ce que les conditions ne puissent pas être satisfaites simultanément. En effet, dans le cas où une condition d'inapplicabilité et une condition de modification sont satisfaites simultanément par exemple, il y a ambiguïté sur l'élément à prendre en compte. Il est toutefois possible de définir plusieurs conditions pour une même section lorsque celles-ci sont compatibles.

---
_ℹ Pourquoi `condition de non-application` plutôt que `condition d'application` ?_

_C'est principalement à cause très complexes, comme le 1510. En effet, dans les annexes, il est indiqué que tel paragraphe ne s'applique pas pour les installations à enregistrement et mises en service avant telle date. Cette prescription est également référencée dans les autres annexes avec d'autres conditions d'application. Il est donc difficile de reconstituer la liste des cas d'application (il faudrait aller d'annexe en annexe pour chaque paragraphe) et il est plus facile d'ajouter un cas de non application à chaque fois (la liste des conditions d'application finales est donc constituée automatiquement)._
