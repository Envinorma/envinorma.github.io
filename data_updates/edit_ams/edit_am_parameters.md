---
title: Editer le paramétrage
permalink: /data/edit_ams/edit_am_parameters
parent: Modifier les AMs
grand_parent: Mise à jour des données
nav_order: 6
---

# Editer le paramétrage de l'arrêté

Un AM peut être inapplicable à une certaine condition. Par exemple, un AM peut être inapplicable lorsque la date de mise en service de l'installation est antérieure à une certaine date.

Il se peut également que l'on souhaite associer l'AM a des avertissements. Par exemple, on peut vouloir signaler qu'un AM n'est pas applicable si l'exploitant n'en a pas fait la demande.

Les paragraphes d'un AM peuvent être associés à des paramètres. Il y a plusieurs cas de figure :

- `Section non applicable` : un paragraphe (ou certains alinéas d'un paragraphe) ne s'applique pas dans certaines conditions
- `Section modification` : un paragraphe peut être modifié dans certaines conditions
- `Avertissement` : un paragraphe peut être accompagné d'un avertissement (lorsque les deux cas précédents ne suffisent pas)

Pour tout ce qui touche à la modification du paramétrage :

- Se rendre sur la page d'accueil du back office et cliquer sur l'AM souhaité
- Cliquer sur l'onglet `Paramétrage`
- Cliquer sur le bouton `Editer le paramétrage`

Selon l'action souhaitée, suivre les indications des paragraphes suivants.

> NB : pour que le nouveau paramétrage soit effectivement modifié dans Envinorma, il faut [mettre à jour les AMs envinorma](/data/am).

## Modifier le cas d'inapplicabilité et les avertissements d'un AM

- Dans l'encadré `Paramètres concernants l'arrêté en entier`, cliquer sur le bouton `Editer`
- Remplir le formulaire, puis valider

> NB : Les cas d'applicabilité dépendant de la rubrique, du régime et de l'alinéa ne doivent pas être renseignés ici mais dans les [metadonnées](/data/edit_ams/edit_am_metadata).

## Déclarer une section non applicable

- Cliquer sur le bouton `Nouvelle inapplicabilité` ou copier une inapplicabilité existante (affichée sous le titre `Paramètres`)
- **Paragraphe visé** : Choisir le titre du paragraphe visé par la condition et cocher les alinéas inapplicables. Cocher `Rendre inapplicable les sous-sections ?` si les sous-sections du paragraphe visés doivent également être rendues inapplicables.

> NB : il est possible de viser plusieurs sections en cliquant sur `Ajouter un paragraphe`

- **Condition** : la description de la condition à satisfaire pour déclencher l'inapplicabilité

## Déclarer une section modifiée

- Cliquer sur le bouton `Nouvelle section alternative` ou copier une section alternative existante (affichée sous le titre `Paramètres`)
- **Paragraphe visé** : Choisir le titre du paragraphe visé par la condition et écrire la nouvelle version du paragraphe

> NB : il est possible de renseigner plusieurs sections alternatives en cliquant sur `Ajouter un paragraphe`

- **Condition** : la description de la condition à satisfaire pour déclencher la modification

## Déclarer un avertissement

- Cliquer sur le bouton `Nouvel avertissement` ou copier un avertissement existant (affiché sous le titre `Paramètres`)
- **Paragraphe visé** : Choisir le titre du paragraphe visé par la condition

> NB : il est possible d'associer l'avertissement à plusieurs sections en cliquant sur `Ajouter un paragraphe`

- Renseigner le contenu de l'avertissement

## Modifier les paramètres existants

Tous les paramètres peuvent être modifiés ou supprimer en cliquant sur les boutons `Editer ou supprimer`

---

### ⚠️ Ne pas sur-paramétrer

Lorsque la condition est assez évidente et précisée dans le paragraphe concernée, il est inutile de la renseigner. Il est intéressant de renseigner une modification/non-application si son absence entraverait la lecture ou pourrait être source d'erreur.

### ℹ Pourquoi `condition de non-application` plutôt que `condition d'application` ?

C'est principalement à cause des AM très complexes, comme le 1510. En effet, dans les annexes, il est indiqué que tel paragraphe ne s'applique pas pour les installations à enregistrement et mises en service avant telle date. Cette prescription est également référencée dans les autres annexes avec d'autres conditions d'application. Il est donc difficile de reconstituer la liste des cas d'application (il faudrait aller d'annexe en annexe pour chaque paragraphe) et il est plus facile d'ajouter un cas de non application à chaque fois (la liste des conditions d'application finales est donc constituée automatiquement).
