# Importer des images

![image](../images/v1/projet-vide.png)

Une fois un projet créé ou ouvert, la fenêtre principale de Panoptic s'ouvre.

Pour importer des images, il faut cliquer sur "**+ Ajouter une source d'images**" en haut à gauche, dans la section "Dossiers". Une fenêtre s'ouvre et propose deux types de sources : un dossier présent sur votre ordinateur ("Dossier local") ou une collection IIIF ("IIIF").

![image](../images/v1/source-images.png)

## Importer un dossier local

Cliquez sur "Dossier local", puis naviguez dans l'explorateur jusqu'au dossier où se trouvent les images que vous souhaitez importer. Le nombre d'images contenues dans chaque dossier est indiqué à droite de son nom. Cliquez enfin sur "Sélectionner".

![image](../images/v1/source-dossier.png)

!!! Précision    
    L'import d'un dossier importe également tous les sous-dossiers contenus dans le dossier.

    Vous pouvez importer successivement plusieurs dossiers contenant des images.

    Il ne faudra pas bouger le dossier qui contient les images, ni en renommer le chemin ensuite.

Les dossiers importés apparaissent ensuite dans la section "Dossiers", sous "Disque local", avec le nombre d'images qu'ils contiennent. Les trois petits points à droite d'une source permettent de la resynchroniser (pour prendre en compte des images ajoutées ou supprimées depuis l'import) ou de la retirer du projet.

![image](../images/v1/dossiers.png)

## Importer une collection IIIF

Panoptic peut également importer des images directement depuis un serveur [IIIF](https://iiif.io/). Cliquez sur "IIIF" et collez l'URL d'un manifeste ou d'une collection IIIF (Presentation API v2 ou v3). Le bouton "Tester la connexion" permet de vérifier que l'URL est valide avant de lancer l'import avec "Importer".

![image](../images/v1/source-iiif.png)

Si le serveur demande une authentification, la section "Authentification (optionnelle)" permet de renseigner un jeton, un identifiant et un mot de passe ou une clé d'API.

## Suivi de l'import

![image](../images/v1/taches.png)

Une fois que vous avez sélectionné le ou les dossiers d'images à importer, le temps d'import et de calcul peut prendre plusieurs minutes. Cela dépend de la puissance de votre ordinateur et du nombre d'images importées. 

Vous pouvez suivre l'avancée des calculs en haut de l'écran, à droite du nom du projet : une barre de progression indique la tâche en cours. En cliquant dessus, la liste des tâches s'affiche avec, pour chacune, le nombre d'images traitées et la vitesse de calcul. Il est possible d'arrêter une tâche en cours depuis cette liste.

!!! Important
    Important ! Pour que les images soient vectorisées lors de leur import, il faut avoir au préalable [installé le module "PanopticML"](/install/install_plugin/).

!!! Rappel 
    A quoi sert la vectorisation des images ? Dans les grandes lignes, la vectorisation des images est un préalable nécessaire à la recherche d'images similaires les unes aux autres, en fonction de leur contenu formel (ce que l'on voit dans les images).
