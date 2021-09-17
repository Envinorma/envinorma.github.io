---
title: Créer un nouvel AM
permalink: /data/edit_ams/create_am
parent: Modifier les AMs
grand_parent: Mise à jour des données
nav_order: 1
---

# Créer un nouvel arrêté ministériel

- Cliquer sur le bouton `+ Créer un arrêté` sur la page d'accueil du back office
- Remplir l'identifiant Légifrance de l'arrêté à créer. Celui-ci peut être retrouvé dans l'URL de l'arrêté. Il commence par `LEGITEXT` ou `JORFTEXT`.

> Par exemple, pour l'arrêté consultable sur l'URL [https://www.legifrance.gouv.fr/jorf/id/JORFTEXT000034429274](https://www.legifrance.gouv.fr/jorf/id/JORFTEXT000034429274), l'identifiant Légifrance est `JORFTEXT000034429274`.

> NB : À des fins de tests, il est possible de créer un AM à partir de n'importe quel identifiant commençant par `FAKE`.

- Cliquer sur le bouton `Créer un nouvel AM`. Si l'identifiant Légifrance renseigné précedemment correspond à un AM existant, cette action redirige vers la modification de l'AM existant.
- Remplir le formulaire en suivant les différentes consignes. Le statut de l'AM doit généralement être choisi comme étant `EN CREATION`, ce qui permet de travailler sur l'AM sans l'exploiter sur Envinorma tant que l'AM n'est pas terminé.
- Valider le formulaire
- Maintenant que les renseignements généraux sur l'AM ont été créés (les metadonnées), il faut :
  1. [Créer le contenu de l'AM](/data/edit_ams/edit_am_content)
  2. [Définir le paramétrage](/data/edit_ams/edit_am_parameters)
  3. [Associer les thèmes aux sections](/data/edit_ams/edit_am_topics)
- Une fois ces trois étapes effectuées, il faut penser à modifier les metadonnées de l'AM pour déclarer l'AM comme `en vigueur` pour qu'il soit utilisable par Envinorma.

> NB : Pour que le nouvel AM soit effectivement utilisable dans Envinorma, il faut [mettre à jour les AMs envinorma](/data/am).
