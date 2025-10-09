# Questions fréquentes

## Est ce que panoptic créé les corpus d'image automatiquement ? 

Non panoptic est un outil **d'analyse** de corpus déjà existant. Pour être utilisé il faut préalablement avoir téléchargé son corpus d'images **localement**. 

## Mon corpus est en IIIF, puis-je l'importer dans panoptic ? 

Pour le moment non, mais nous y travaillons.

## Je n'arrive pas à importer mes données additionnelles dans panoptic

Assurez vous d'avoir [bien respecté le tutoriel](/start/propsimport)

La plupart des erreurs viennent couramment de:

- la première colonne doit impérativement se nommer path et contenir un chemin vers l'image
- la colonne path doit seulement s'appeler path et rien d'autre
- il ne doit pas y avoir en même temps de colonne path et de colonne id
- chaque colonne autre que path doit avoir entre crochets un type de propriété de renseigné

## Puis-je utiliser une carte graphique avec panoptic ? 

Oui c'est possible, lors de l'installation si vous avez une carte graphique NVidia il vous sera proposé d'installer les librairies compatibles GPU. 
Il est à noter que cela n'augmentera que le calcul des vecteurs d'images qui n'a lieu qu'une fois. 

## Si mes images ont déjà été importées, puis-je les partager sans avoir à refaire le calcul ? 

Le calcul des images peut être long, aussi si plusieurs personnes ont vocation à travailler sur un même projet, l'import peut être fait sur un ordinateur ayant de bonnes capacités de calcul, puis le fichier .db peut être partagé, celui ci se trouve dans le dossier que vous avez choisi au moment de la création du projet. 

## Puis-je annoter à plusieurs en ligne sur panoptic ? 

Non, panoptic est un outil fait pour être utilisé localement, nous avons pour but plus tard de le rendre collaboratif mais cela va demander encore beaucoup de développements. 

## Où est ce que Panoptic stocke les données ? 

Lorsque vous créez un projet, vous choisissez un dossier dans lequel le créer, ce dossier contiendra toute la base de donnée sqlite (le fichier panoptic.db) ainsi que les éventuelles données des plugins. C'est ce fichier .db que vous pouvez utiliser pour partager un projet à quelqu'un d'autre ou pour sauvegarder un projet ailleurs que sur votre ordinateur (pour faire un backup).
