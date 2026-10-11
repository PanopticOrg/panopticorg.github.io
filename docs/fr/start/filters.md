# Manipuler les Images à partir de leurs propriétés

!!! Important
    Préalable nécessaire au (ré)agencement d’un corpus :

    Pour faire des FILTRES, des TRIS ou des GROUPES, des PROPRIÉTÉS doivent exister et être remplies. Par exemple, on a réalisé de premières annotations d’images du corpus de façon thématique : "papillon", "sport"... Autre exemple, on a importé au préalable des données associées aux images, qui sont constituées en tant que propriétés lors de leur import.

Ces différentes fonctionnalités sont des fonctionnalités d'exploration visuelle : tout se passe à l'écran, les (ré)agencements ne sont ni définitifs, ni destructifs du corpus. On peut constamment les annuler, les refaire, les modifier... On peut aussi multiplier ces (ré)agencements, pour explorer son corpus de différentes manières, grâce à la possibilité de créer différents onglets au sein de Panoptic.

Les (ré)agencements peuvent être réalisés à n'importe quel moment de l'exploration. On peut aussi les prévoir à l'avance, une fois les propriétés créées, mais avant d'avoir annoté quoique ce soit. Si l'on annote au cours du travail, le corpus se réagence dans la fenêtre en temps réel : une image annotée rejoint directement le groupe correspondant.

Les filtres, groupes et tris se gèrent depuis la barre située au-dessus des images. Ils peuvent aussi être ajoutés directement depuis la section "Propriétés", en survolant une propriété et en cliquant sur l'icône d'entonnoir (filtrer), de tri ou de groupe qui apparaît à côté de son nom.

## Filtrer

![image](../images/v1/filtres.png)

- Appuyez sur le “+” à côté de "Filtrer".
- Sélectionnez la propriété à partir de laquelle vous voulez filtrer les images. 
- Choisissez la condition (par exemple "contient", "est vide", "n'est pas vide", "=", "<"...) puis la valeur. Vous définissez ici les conditions d’affichage des images.
- Cliquez sur "Appliquer".

Plusieurs filtres peuvent être combinés avec "+ Filtre", et regroupés avec "+ Groupe de filtres". Il est alors possible de choisir s'ils doivent tous être respectés ("et") ou si un seul suffit ("ou"). Pour supprimer un filtre, cliquez sur l'icône de corbeille à sa droite.

### Pourquoi filtrer ?

Les filtres peuvent être pratiques dans différents cas. Pour prendre un exemple, vous pouvez choisir de filtrer les images que vous avez déjà annoté, pour n’afficher que celles que vous devez encore travailler.

Autre exemple, vous pouvez également créer une propriété de type CHECKBOX ("case à cocher"), la nommer "hors sujet" ou encore "annotation réalisée ?", et décider que les images ne s’affichent plus dans l’onglet Panoptic actif dès lors que vous avez coché la case.

## Grouper

![image](../images/v1/grouper.png)

En cliquant sur le "+" à côté de "Grouper", sélectionnez la propriété à partir de laquelle vous voulez faire le groupage d’images. Une fois la propriété sélectionnée, les groupes se constituent directement à l’écran, dans le panneau central de Panoptic, suivant le critère donné.

### Réordonner les groupes entre eux :

Lorsque l’on ajoute un type de groupage, celui-ci s’indique à côté de l’option "Grouper". Il est possible de changer le type de tri (nombre d’éléments, alphabétique) et l’ordre (croissant ou décroissant) en cliquant sur les flèches afférentes.

### Groupes et sous-groupes :

![image](../images/v1/grouper2.png)

Il est possible de faire des groupes dans les groupes, par exemple en groupant par une propriété importée en métadonnée, le nom de l'artiste par exemple, puis par une propriété thématique (ce que l’on a annoté pour décrire l’image avec un mot clé, ou ici le genre de l'oeuvre).

### Supprimer un groupe :

Pour supprimer un groupe, il suffit de cliquer sur le nom de la propriété que l’on veut supprimer, à côté de l’option "Grouper".

### Faire des clusters dans un groupe :

Il est possible de faire des clusters d’images similaires au sein d’un même groupe d’images afin de le réagencer, depuis le menu des trois petits points à côté du nom du groupe (voir [les clusters](/start/clusters/)).

## Trier

![image](../images/v1/tri.png)

- Appuyez sur le "+" à côté de "Trier".
- Sélectionnez la propriété à partir de laquelle vous voulez trier les images.

Il est possible de les agencer par ordre alphabétique, ou encore de façon chronologique par exemple. La flèche à côté du nom de la propriété permet d'inverser l'ordre du tri.

Il est possible de combiner des fonctions de GROUPAGE, de FILTRE et de TRI : on peut alors réaliser des groupes en fonction de certaines propriétés, et trier les images rangées dans ces groupes en fonction d’autres propriétés. Dans l'exemple ci-dessus, on n'affiche que les oeuvres impressionnistes (filtre sur "mouvement"), groupées par artiste, et triées par largeur ("width").

## Rechercher

La barre de recherche, en haut à gauche, permet de chercher un texte dans toutes les propriétés des images. Le menu déroulant à gauche de la barre permet de choisir le mode de recherche : "Text" pour une recherche simple, "Regex" pour une recherche par expression régulière, ou une recherche par similarité textuelle fournie par le plugin de similarité (voir [la similarité textuelle](/start/text/)). Le raccourci ctrl + F place directement le curseur dans la barre de recherche.

![image](../images/v1/recherche-modes.png)
