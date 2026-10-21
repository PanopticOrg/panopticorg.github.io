# Les vues

Panoptic propose plusieurs façons d'afficher les images, appelées [vues](/concepts/#vues). On choisit la vue dans le menu situé en haut à gauche des images. Chaque [onglet](/advanced/onglets/) garde sa propre vue, en plus de ses filtres, tris et groupes.

![Alt text](../images/v1/vues.png)

À droite du nom de la vue, le curseur permet de régler la taille des images et l'icône d'oeil d'afficher ou de masquer les propriétés sous les images.

## La vue grille
La vue par défaut, affiche une simple grille d'images.

## La vue tableau

Une vue sous forme de tableau classique, elle permet de se concentrer plus sur les propriétés accompagnant les images, notamment les propriétés de type texte pouvant prendre de la place. Chaque propriété affichée devient une colonne, dont la largeur peut être ajustée.

![Alt text](../images/v1/vue-tableau.png)

## La vue graphique

Vue permettant d'afficher des graphiques montrant le nombre d'images contenues dans un groupage : le premier niveau de groupe devient l'axe horizontal. Exemple, si je groupe mes images par mouvement artistique et passe en vue graphique, je peux afficher le nombre d'images pour chaque mouvement, ainsi qu'une prévisualisation des images en survolant une barre ou un point. Les boutons en haut à gauche permettent de choisir entre courbes, aires et barres, et d'afficher une vignette sur chaque point. Il est aussi possible de cliquer ou de glisser sur le graphique pour sélectionner les images correspondantes.

![Alt text](../images/v1/vue-graphe.png)

!!! note

    Il est à noter que tous les filtres et tris sont également appliqués en temps réel dans cette vue, ce qui vous permet de modifier votre graphique à la volée en fonction d'autres propriétés que vous auriez.
    De même le groupage par date permet de changer la granularité du groupage en choisissant à la minute, heure, jour, semaine, mois, année. Ces changements sont également répercutés sur le graphe.

Il est également possible de rajouter un second niveau de groupage permettant de fractionner le graphique en fonction d'une autre propriété : chaque valeur devient alors une série. Ici par exemple on rajoute un groupage par artiste après le groupage par mouvement. On a également choisi les barres et activé l'option "Empiler les séries".

![Alt text](../images/v1/vue-graphe-empilee.png)

## La vue spatiale

La vue spatiale place les images sur une carte en deux dimensions : les images proches visuellement ou sémantiquement sont placées côte à côte. Pour l'utiliser, il faut d'abord créer une carte en cliquant sur "Créer", choisir les vecteurs à utiliser, éventuellement donner un nom à la carte, puis cliquer sur "Lancer".

![Alt text](../images/v1/vue-spatiale-creer.png)

Une fois la carte calculée, on peut s'y déplacer et zoomer à la souris. Dans l'exemple, on distingue nettement les dessins et gravures à gauche, les portraits en haut et les paysages en bas à droite. Le menu déroulant permet de passer d'une carte à une autre si plusieurs ont été créées, et la corbeille de supprimer la carte affichée. Les curseurs à droite de la corbeille règlent la largeur de la bordure des images, la taille de l'agrandissement affiché au survol d'une image et l'écartement des images sur la carte.

À droite de la carte, le panneau "Aperçu" affiche l'image survolée, et la "Minimap" montre l'ensemble de la carte avec, encadrée, la zone affichée : cliquer ou glisser sur la minimap permet de se déplacer rapidement. Chaque section du panneau peut être repliée en cliquant sur son titre.

![Alt text](../images/v1/vue-spatiale.png)

La barre d'outils au-dessus de la carte permet d'afficher les images sous forme de points, de passer en disposition en grille (voir plus bas), de se déplacer (main), ou de sélectionner des images en les entourant au lasso : le clic gauche ajoute les images entourées à la sélection, le clic droit les en retire. Les images ainsi sélectionnées peuvent ensuite être annotées par lots comme dans la grille. Quel que soit l'outil choisi, maintenir la touche espace enfoncée permet de déplacer la carte.

Si les images sont groupées, chaque groupe est entouré d'une couleur différente et la liste des groupes s'affiche dans le panneau de droite. Cliquer sur un groupe de la liste le met en avant sur la carte, et les icônes à droite de son nom permettent de centrer la carte sur ce groupe ou d'y créer des clusters.

![Alt text](../images/v1/vue-spatiale-groupes.png)

### La disposition en grille

Dans les zones denses de la carte, les images se chevauchent et deviennent difficiles à distinguer. L'icône de grille de la barre d'outils range chaque image dans une case d'une grille régulière, sans aucun chevauchement, tout en conservant l'organisation de la carte : des images proches sur la carte restent voisines dans la grille, et des ensembles éloignés restent séparés par des cases vides. Un nouveau clic sur la même icône permet de revenir à tout moment à la disposition d'origine.

![Alt text](../images/v1/vue-spatiale-outils.png)

En mode grille, de nouvelles icônes apparaissent dans la barre d'outils, de gauche à droite après l'icône de grille :

- **Remplir les cases** : recadre chaque image en carré pour qu'elle occupe toute sa case.
- **Contours et noms des groupes** (seulement si les images sont groupées) : trace le contour de chaque groupe et affiche son nom sur la carte lorsque l'on dézoome, pour la lire comme une carte géographique.
- **Sélection par cases** et **Pinceau à tags**, décrits ci-dessous.

Sans aucun groupe, la grille montre simplement les images de la carte rangées côte à côte :

![Alt text](../images/v1/vue-spatiale-grille-simple.png)

En mode grille, le dernier curseur à droite devient "Cases vides entre les groupes" : il règle l'espace laissé entre les ensembles d'images. Plus la valeur est élevée, plus les ensembles éloignés sur la carte sont séparés. En l'augmentant, les grandes zones de la carte (dessins, portraits, paysages…) se détachent nettement les unes des autres :

![Alt text](../images/v1/vue-spatiale-grille-espacee.png)

Si l'on groupe ensuite les images, par exemple après les avoir réparties en [clusters](/start/clusters/), chaque cluster forme une région de la grille, entourée de sa couleur et portant son nom :

![Alt text](../images/v1/vue-spatiale-grille.png)

C'est à partir de cette grille que sont présentés les outils de sélection et d'annotation ci-dessous.

!!! note

    La grille est calculée une seule fois pour toute la carte. Lorsqu'un filtre masque des images, celles-ci laissent simplement leur case vide et les autres images ne bougent pas, ce qui permet de garder ses repères d'un filtre à l'autre.

### La sélection par cases

L'outil de sélection par cases (icône de cadre) affiche un curseur carré qui couvre plusieurs cases de la grille. Il suffit de cliquer ou de glisser sur la carte pour sélectionner toutes les images couvertes, comme avec un pinceau. Les cases parcourues sont colorées pendant le geste, et la sélection est appliquée au relâchement du bouton.

- le clic gauche ajoute les images à la sélection, le clic droit les en retire,
- ctrl + molette change la taille du curseur (le nombre de cases couvertes est affiché en bas de la carte),
- maintenir shift permet de sélectionner un rectangle entre la case de départ et la case courante.

![Alt text](../images/v1/vue-spatiale-cases.png)

Ici, 99 images, essentiellement du cluster Clustering_8.3, ont été sélectionnées en quelques coups de curseur : la barre de sélection apparaît en haut de l'écran et les images peuvent être annotées par lots comme d'habitude (voir [Annoter par lots](/start/annotate/#annoter-par-lots)).

### Le pinceau à tags

Le pinceau à tags (icône de pinceau) fonctionne avec les mêmes gestes que la sélection par cases, mais au lieu de sélectionner les images, il leur attribue directement un tag. Il permet ainsi d'annoter très rapidement toute une zone de la carte.

Lorsque l'outil est actif, une section "Pinceau" apparaît dans le panneau de droite, sous l'aperçu. On y choisit la propriété de type tag ou multitags à annoter, puis le tag à appliquer : comme sous les images, il est possible de rechercher un tag existant ou d'en créer un nouveau à la volée, et de changer sa couleur. La croix à côté du tag permet de le désélectionner.

![Alt text](../images/v1/vue-spatiale-pinceau.png)

Tant qu'un tag est choisi, la carte montre ce qui a déjà été peint : les images qui portent le tag sont entourées de sa couleur, les autres sont grisées. Il suffit ensuite de peindre :

- le clic gauche ajoute le tag aux images couvertes, le clic droit le leur retire,
- ctrl + molette change la taille du pinceau et shift permet de peindre un rectangle, comme pour la sélection par cases.

Pour une propriété de type tag, le tag peint remplace la valeur existante, alors que pour une propriété de type multitags il s'ajoute aux tags déjà présents. Chaque coup de pinceau est enregistré comme une seule modification dans l'historique et peut donc être annulé d'un coup avec ctrl + z.

## La vue recommandations

Cette vue propose des images similaires à un groupe pour le compléter (voir [Les recommandations](/start/reco/)).

## La vue groupée

Cette vue résume chaque groupe ou cluster par une mosaïque de quelques images. Elle est particulièrement utile pour avoir une vue d'ensemble des clusters et pour les annoter avec le bouton "Assigner à…" (voir [Les clusters](/start/clusters/)).

## Diviser la vue

L'icône en haut à droite des images ("Diviser à droite") permet d'afficher une seconde vue à côté de la première, dans le même onglet. On peut ainsi par exemple garder une grille d'images à gauche tout en consultant le tableau des propriétés à droite. Chaque côté a sa propre vue, sa taille d'images et ses propriétés affichées. La même icône, sur la vue de droite, permet de revenir à une seule vue.

![Alt text](../images/v1/vue-divisee.png)
