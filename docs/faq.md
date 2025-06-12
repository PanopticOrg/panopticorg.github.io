# Questions fréquences

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



