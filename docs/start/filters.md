# Manipuler les Images à partir de leurs propriétés

!!! Préalable nécessaire au (ré)agencement d’un corpus
    Pour faire des FILTRES, des TRIS, des GROUPES, des PROPRIÉTÉS doivent exister et être remplies. Par exemple, on a réalisé de premières annotations d’images du corpus de façon thématique : "papillon", "sport"... Autre exemple, on a importé au préalable des données associées aux images, qui sont constituées en tant que propriétés lors de leur import.

Ces différentes fonctionnalités sont des fonctionnalités d'exploration visuelle~: tout se passe à l'écran, les (ré)agencements ne sont ni définitifs, ni destructifs du corpus. On peut constamment les annuler, les refaire, les modifier... On peut aussi multiplier ces (ré)agencements, pour explorer son corpus de différentes manières, grâce à la possibilité de créer différents onglets au sein de Panoptic.

Les (ré)agencements peuvent être réalisés à n'importe quel moment de l'exploration. On peut aussi les prévoir à l'avance, une fois les propriétés créées, mais avant d'avoir annoté quoique ce soit. Si l'on annote au cours du travail, on peut décider d'activer ou non l'actualisation automatique, pour que le corpus se réagence dans la fenêtre en temps réel, ou seulement lorsqu'on le souhaite.

## Filtrer

- Appuyez sur le “+” à côté de FILTRER.
- Sélectionnez la propriété à partir de laquelle vous voulez filtrer les images. Vous définissez ici les conditions d’affichage des images

### Pourquoi filtrer ?

Les filtres peuvent être pratiques dans différents cas. Pour prendre un exemple, vous pouvez choisir de filtrer les images que vous avez déjà annoté, pour n’afficher que celles que vous devez encore travailler.

Autre exemple, vous pouvez également créer une propriété de type CHECKBOX ("case à cocher"), la nommer "hors sujet" ou encore "annotation réalisée ?", et décider que les images ne s’affichent plus dans l’onglet Panoptic actif dès lors que vous avez coché la case.

## Grouper

En cliquant sur le "+" à côté de la fonction GROUPE, sélectionnez la propriété à partir de laquelle vous voulez faire le groupage d’images. Une fois la propriété sélectionnée, les groupes se constituent directement à l’écran, dans le panneau central de Panoptic, suivant le critère donné.

### Réordonner les groupes entre eux :

Lorsque l’on ajoute un type de groupage, celui-ci s’indique à côté de l’option GROUPER. Il est possible de changer le type de tri (nombre d’éléments, alphabétique) et l’ordre (croissant ou décroissant) en cliquant sur les flèches afférentes.

### Groupes et sous-groupes :

Il est possible de faire des groupes dans les groupes, par exemple en groupant par une propriété thématique (ce que
l’on a annoté pour décrire l’image avec un mot clé), puis par une propriété importée en métadonnée, le nom du/de la
photographe par exemple.

### Supprimer un groupe :

Pour supprimer un groupe, il suffit de cliquer sur le nom de la propriété que l’on veut supprimer, à côté de l’option GROUPER.

### Faire des clusters dans un groupe :

Il est possible de faire des clusters d’images similaires au sein d’un même groupe d’images afin de le réagencer.

## Trier

- Appuyez sur le "+" à côté de "TRIER".
- Sélectionnez la propriété à partir de laquelle vous voulez trier les images.

Il est possible de les agencer par ordre alphabétique, ou encore de façon chronologique par exemple.

Il est possible de combiner des fonctions de GROUPAGE et de TRI : on peut alors réaliser des groupes en fonction de certaines propriétés, et trier les images rangées dans ces groupes en fonction d’autres propriétés. Le tri à l’intérieur de groupes peut par exemple être réalisé à partir de la propriété calculée par Panoptic "average hash". Il s’agit d’un calcul de similarités sommaire. Cela peut par exemple permettre de trier les photos d’un-e même photographe (grouper par "auteur") en fonction de leurs ressemblances générales (trier par "average hash").