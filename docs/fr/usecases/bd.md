---
title: "Récits picturaux : du code à la transgression"
---

## Corpus

Le corpus est composé d'images de personnages de bande dessinée.

C'est un corpus adjacent au corpus principal.
L'objet principal étant de réaliser l'annotation, sur plusieurs axes sémantiques, de personnages issus de récits picturaux. Les BDs sont issues de France, Belgique, Cote d'ivoire, et de la RDA.

L'idée de ce sorpus adjacant est avant tout de permettre la visualisation des oppositions entre les personnages sur les diverses catégories d'annotation.

Il y a une centaine d'annotations dont la pluspart placent les personages sur un spectre.

## Question de recherche 

Nous cherchons à étudier le langage iconique au sein de récits picturaux. L'idée étant de déceler les codes ainsi que leurs trangressions.

## Usage de panoptic

### Ce que je m'attendais à trouver dans panoptic et dont je me suis servi

Panoptic a servi a filtrer et grouper les personnages, soit sur nos annotations, soit sur le contexte de production de l'œuvre. Par la suite, nous pouvons utiliser des tris pour ordonner les persos et ainsi comparer leurs annotations.
Ayant un total de 418 personnages, nous aurions pu placer tous les persos d'un coup sur un axe (à l'aide d'un tri), cependant cela aurait donné un résultat que peu lisible. À l'aide des groupes, nous avons alors pu alors séparer les persos par œuvre, franchise, contexte de production, ou encore en fonction d'autres annoations (identité de genre, animaux/humains, ...).

![usage de panoptic pour un corpus de bd](../../images/bd_clair.jpg)

### Ce que je ne m'attendais PAS à trouver dans panoptic et dont je me suis servi

En parallèle, nous voulions tirer des corrélations de ces annotations. On a fait des petits scripts python pour faire toutes nos stats et visualisations. Ces derniers nous permettent de calculer les corélations entre chaque axe d'annotation et les autres, mais aussi de comparer plusieurs axes, ou de le faire sur une partie des personnages seulement.
L'arrivée des plugins dans panotpic nous a alors donné l'idée d'interfacer nos scripts de visualisations pour  avec panoptic dans l'idée de permettre à n'importe qui d'utiliser notre code. Cependant, nous ne nous y sommes pas encore attelés.

L'interface web de panoptic nous a également permis de déployer le tout sur un serveur, ça permettait de consulter les annotations à plusieurs, mais également de facilement le montrer en colloque et autres.

### Ce que je m'attendais à trouver et qu'il n'y avait PAS / Quelles difficultés ai-je rencontrées ?

Afin de continuer l'annotation de nos données, nous aurions aimé deux choses : avoir des annoations numériques mais continues, avec un slider; et pouvoir annoter à plusieurs à partir d'une seule instance en gardant l'information de qui a annoté quoi.