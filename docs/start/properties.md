# Les Propriétés

Pour donner du sens aux images étudiées dans l’interface de Panoptic, cela se fait en créant et définissant un ensemble de PROPRIÉTÉS. C’est à partir des propriétés créées que vous pouvez annoter les images. Ces propriétés sont de plusieurs types (en anglais) : 

- text, 
- numeric, 
- tag, 
- multi_tags, 
- checkbox (case à cocher),
- url, 
- date,
- color.

Une fois les propriétés créées, vous pouvez associer des annotations à chaque image séparément, ou bien à des lots d’images, en lien avec une propriété particulière, ou bien avec plusieurs propriétés. Les propriétés peuvent être créées au fur et à mesure, et pas nécessairement définies en amont.

## Créer et afficher une propriété

Pour annoter vos images, il faut au préalable créer au moins une propriété, qui contiendra des annotations de types spécifiques (tag, date, text, number...)
    
Pour créer une propriété (par exemple de type "MultiTags") :
     
- À gauche, cliquez sur "Nouvelle propriété".
-  Nommez la propriété, choisissez son type et choisissez s'il s'agit d'une propriété d'image ou d'instance. Faites "Confirmer".
- Affichez (ou masquez) la propriété créée en cliquant sur l'icône d'oeil situé à côté de son nom.

!!! à savoir
    Il n'est pas nécessaire de définir en amont les propriétés dont vous aurez besoin au cours du travail. Celles-ci peuvent être créées au fur et à mesure.

## Relations entre propriétés

Il est possible de définir des relations hiérarchiques (parent-enfant) entre annotations, pour les propriétés de type Tag et MultiTags.

## Les Propriétés Panoptic

Les "PROPRIÉTÉS PANOPTIC" sont des propriétés non manipulables. Elles sont calculées par le logiciel lors de
l’import des images, et vous fournissent quelques métriques : un identifiant uniquement pour chaque image
("ID"), une signature propre à chaque image, pour repérer les doublons parfaits ("sha1"), une signature
propre aux images grossièrement similaires ("average hash"), leur dossier d’origine sur votre ordinateur
("folder"), ainsi que leur chemin absolu ("path"), et enfin leurs dimensions ("width" et "height")