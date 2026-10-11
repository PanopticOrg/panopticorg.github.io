# Questions fréquentes

## Est ce que panoptic créé les corpus d'image automatiquement ? 

Non panoptic est un outil **d'analyse** de corpus déjà existant. Pour être utilisé il faut préalablement avoir téléchargé son corpus d'images **localement**, ou disposer de l'adresse d'une collection IIIF.

## Mon corpus est en IIIF, puis-je l'importer dans panoptic ? 

Oui, depuis la v1. Il suffit de cliquer sur "Ajouter une source d'images" puis sur "IIIF" et de coller l'URL du manifeste ou de la collection (voir [Importer des images](/start/images/#importer-une-collection-iiif)).

## Je n'arrive pas à importer mes données additionnelles dans panoptic

Assurez vous d'avoir [bien respecté le tutoriel](/start/propsimport)

La plupart des erreurs viennent couramment de:

- la première colonne doit impérativement se nommer path (ou id) et contenir un chemin vers l'image (ou son identifiant Panoptic)
- la colonne path doit seulement s'appeler path et rien d'autre
- il ne doit pas y avoir en même temps de colonne path et de colonne id
- chaque colonne autre que path doit avoir entre crochets un type de propriété de renseigné
- le séparateur doit être un point-virgule ( ; ) et le fichier doit être encodé en UTF-8

## Puis-je utiliser une carte graphique avec panoptic ? 

Oui c'est possible, lors de l'installation si vous avez une carte graphique NVidia il vous sera proposé d'installer les librairies compatibles GPU. 
Il est à noter que cela n'accélérera que le calcul des vecteurs d'images qui n'a lieu qu'une fois. 

## Si mes images ont déjà été importées, puis-je les partager sans avoir à refaire le calcul ? 

Le calcul des images peut être long, aussi si plusieurs personnes ont vocation à travailler sur un même projet, l'import peut être fait sur un ordinateur ayant de bonnes capacités de calcul, puis le dossier du projet peut être partagé, celui ci se trouve dans le dossier que vous avez choisi au moment de la création du projet (voir [Partager un projet](/advanced/projectimport/)). 

## Puis-je annoter à plusieurs en ligne sur panoptic ? 

Non, panoptic est un outil fait pour être utilisé localement. Il peut toutefois être installé sur un serveur pour être utilisé depuis le navigateur d'un autre ordinateur (voir [Installation Serveur](/install/install_server/)). Il est en revanche possible de créer plusieurs utilisateurs pour travailler à tour de rôle sur un même projet et retrouver qui a fait quelle modification (voir [Utilisateurs](/start/projets/#utilisateurs)). 

## Où est ce que Panoptic stocke les données ? 

Lorsque vous créez un projet, vous choisissez un dossier dans lequel le créer, ce dossier contiendra toutes les bases de données sqlite du projet (data.db pour les annotations, media.db pour les miniatures et les vecteurs, project.db pour les onglets et les paramètres) ainsi que les éventuelles données des plugins. C'est ce dossier que vous pouvez utiliser pour partager un projet à quelqu'un d'autre ou pour sauvegarder un projet ailleurs que sur votre ordinateur (pour faire un backup).

La liste des projets et des plugins installés est quant à elle enregistrée dans le fichier `~/.panoptic/panoptic.db`.

## J'ai des projets créés avec une ancienne version de Panoptic, puis-je les ouvrir avec la v1 ?

Oui, après les avoir convertis. Panoptic détecte ces projets au lancement et propose de les convertir depuis la page d'accueil. La conversion crée une copie du projet et laisse l'original intact (voir [Projets créés avec une ancienne version](/start/projets/#projets-crees-avec-une-ancienne-version)).
