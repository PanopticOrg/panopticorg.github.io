# Astuces et raccourcis

Cette section vise à recenser quelques raccourcis claviers et astuces d'utilisation permettant de faciliter l'usage de panoptic. 

## Raccourcis

!!! note

    A noter que sur mac, CTRL est remplacé par Commande

- **ctrl + z:** annuler, 
- **ctrl + shift + z:** rétablir, 
- **ctrl + f:** place le curseur dans la barre de recherche,
- **ctrl maintenu au survol d'une image:** affichage d'un agrandissement d'une image, 
- **sélection en maintenant shift:** sélectionne toutes les images entre la première et la dernière image sélectionnée,
- **sélection en maintenant ctrl:** sélectionne une image sans annuler la sélection en cours
- **tab lorsque l'on est en train d'annoter une image:** passe à l'annotation de la même propriété sur l'image d'après, 
- **entrée permet de valider la plupart des actions (annotation, clusters, executer etc.)**
- **espace maintenu dans la vue spatiale:** déplace la carte, quel que soit l'outil sélectionné,
- **ctrl + molette avec la sélection par cases ou le pinceau à tags:** change la taille du curseur (voir [La vue spatiale](/advanced/onglets/#la-vue-spatiale)).

## Historique des modifications

L'icône d'horloge à droite du nom du projet ouvre l'historique des modifications. Chaque ligne correspond à une action (par exemple "119 tag(s) modifié(s)"), et les flèches en haut permettent d'annuler ou de rétablir les dernières actions, comme avec ctrl + z. L'onglet "Mes modifications" n'affiche que les actions de l'utilisateur en cours, et "Tous les utilisateurs" celles de toutes les personnes ayant travaillé sur le projet (voir [Utilisateurs](/start/projets/#utilisateurs)).

![Alt text](../images/v1/historique.png)

## Astuces

- lorsque l'on effectue une recherche de similarité par texte, si l'on entre une url d'image à la place du texte, panoptic va télécharger cette image et faire une recherche de similarité par image sur cette image externe.
- l'icône d'image à gauche de la barre de recherche permet de passer du mode "Instance" (toutes les instances d'une image sont affichées) au mode "Image" (chaque image n'est affichée qu'une seule fois). Voir [Comprendre les instances](/advanced/instances/).

![Alt text](../images/v1/mode-image-instance.png)
