# La fenêtre de gestion des tags

La fenêtre (ou modal) de gestion des tags permet de manipuler avec plus de facilité les tags afin de pouvoir:

- les renommer, changer leur couleur ou les supprimer
- gérer les liens de hiérarchie
- fusionner des tags si l'on estime cela nécessaire

Il existe deux vues possibles, accessibles par les icônes en haut à gauche de la fenêtre:

- la vue liste, vue par défaut qui permet d'afficher la liste des tags, de les trier par ordre alphabétique ou par nombre d'images associée à ces tags![Alt text](../images/v1/tags-liste.png)
- la vue arbre, qui est plus visuelle et est particulièrement utile lorsque l'on cherche à comprendre l'organisation hiérarchique des tags ![Alt text](../images/v1/tags-arbre.png)

Les onglets à droite de ces icônes permettent de passer d'une propriété de type tag ou multitags à une autre sans fermer la fenêtre. Le nombre affiché à côté de chaque propriété correspond au nombre d'images annotées.

## Accès

Pour ouvrir cette fenêtre il suffit de survoler une propriété de type tag ou multitags dans la section "Propriétés" puis de cliquer sur le logo d'agrandissement qui apparaît à côté de son nom:
![Alt text](../images/v1/propriete-survol.png)

## Trier les tags

Dans la vue liste, il est facile de filtrer les tags en cherchant dans le champ recherche (icône de loupe), ou encore de les trier en prenant en compte soit leur nom soit le nombre d'images associées à chaque tag. 

Il suffit pour cela d'utiliser les boutons de tri, à droite de l'icône de loupe en haut de chaque colonne.

## Créer, renommer et supprimer des tags

Pour créer un nouveau tag, cliquez sur la loupe d'une colonne, entrez le nom du tag puis appuyez sur entrée ou cliquez sur "Create Tag". Créé depuis la colonne "Tags enfants", le nouveau tag devient directement enfant du tag sélectionné.

Au survol d'un tag sélectionné, l'icône de corbeille permet de le supprimer, et les trois petits points de le renommer ou de changer sa couleur.

## Sélection multiple

Lorsque l'on clique sur un tag, ses images associées s'affiche à droite. Mais il est également possible de sélectionner plusieurs tags à la fois, en maintenant la touche controle (ou shift pour sélectionner une plage de tags), les images associées à tous les tags sélectionnés s'affichent alors en même temps, ce qui peut être pratique pour comparer des tags.

## Fusion

Lorsque plusieurs tags sont sélectionnés il est possible de les fusionner en cliquant sur "Merge Tags", au-dessus des images. Le tag "résultant de la fusion" sera le premier tag sélectionné. Il est possible de fusionner autant de tags à la fois que l'on souhaite. Tous les liens de parentés seront également conservés.

![Alt text](../images/v1/tags-fusion.png)

## Créer des liens de hiérarchie

Comme énoncé sur la page précédente il est possible de créer des liens de hiérarchie entre les tags. Cette opération se fait dans la vue liste : sélectionnez un tag, puis prenez un autre tag dans la colonne "Tous les tags" et glissez-le dans la colonne souhaitée ("Tags parents" ou "Tags enfants"). Dans l'exemple ci-dessous, "forêts" et "marines" ont été glissés dans les enfants de "paysages".

![Alt text](../images/v1/tags-liste.png)

La vue arbre permet ensuite de vérifier d'un coup d'oeil l'organisation obtenue, les parents à gauche et les enfants à droite. Il est aussi possible d'y créer un lien directement : cliquez sur le tag parent, maintenez le bouton de la souris enfoncé et relâchez-le sur le tag enfant. Comme toute modification, un lien créé par erreur peut être annulé avec ctrl + z.
