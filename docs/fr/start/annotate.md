# Annoter les propriétés

Une fois une propriété créée et affichée, il est possible d'annoter les images importées.

Lorsqu'une propriété est affichée, une ligne "Vide..." est affichée en dessous de chaque image. Si l'on affiche deux propriétés, il y en aura deux d'afficher sous chaque image, etc.

## Annoter une image

 Pour annoter une seule image, il suffit de cliquer sur l'espace "Vide..." associé à la bonne propriété sous l'image, et de compléter par l'annotation que l'on souhaite. Pour une propriété de type Tag ou MultiTags, appuyez sur entrée ou cliquez sur "Créer" pour créer le tag.

![](../images/v1/annoter1.png)

Une fois une annotation créée, celle-ci est automatiquement proposée pour les prochaines annotations, avec le nombre d'images qui la portent déjà.

![](../images/v1/annoter2.png)

## Annoter par lots

Il est possible d'annoter les images par lots. Lorsque l'on passe la souris sur une image, une coche cliquable s'affiche en haut à gauche de l'image. En cliquant, la coche devient bleue : l'image est sélectionnée. On peut comme cela en sélectionner plusieurs. Il est possible de sélectionner toutes les images situées entre deux images, en sélectionnant ces deux images tout en maintenant la touche maj/shift appuyée.

Lorsque plusieurs images sont ainsi sélectionnées, apparaît en haut à droite de Panoptic une barre de sélection indiquant le nombre d'images sélectionnées. En cliquant sur l'icône "pot de peinture" de cette barre, un panneau s'ouvre avec toutes les propriétés du projet. Pour chaque propriété, choisissez une valeur puis indiquez s'il faut l'ajouter aux valeurs existantes ("+"), remplacer les valeurs existantes, ou au contraire la retirer ("-"). Cliquez enfin sur "Appliquer" et les images seront annotées.

![](../images/v1/annoter-lots.png)

!!! Attention

    Une fois les images annotées de cette manière, pensez bien à désélectionner les images sélectionnées pour ne pas les réannoter plus tard. Pour les désélectionner, cela se fait en cliquant sur la croix (x) à gauche du nombre d'images sélectionnées.

## Annoter un cluster d'images similaires

### Annoter un cluster en entier

Pour réaliser des clusters d'images similaires, voir la documentation sur les [clusters](https://panopticorg.github.io/start/clusters/).

Il est possible d'annoter tout un cluster en survolant son nom puis en cliquant sur l'icône "pot de peinture" ("Appliquer des propriétés au groupe") qui apparaît à côté. Cette option est aussi disponible dans le menu des trois petits points.

Dans le panneau qui s’ouvre, choisissez la valeur souhaitée pour la propriété, un tag déjà existant ou un nouveau tag. Enfin, faites "Appliquer".

![](../images/v1/groupe-menu.png)

La vue "Groupée" est particulièrement pratique pour annoter des clusters : chaque cluster y est présenté sous forme de mosaïque, avec un bouton "Assigner à…" en dessous. Cliquez dessus et choisissez la propriété dans laquelle enregistrer les annotations (ou créez-en une avec "Nouvelle propriété…").

![](../images/v1/assigner-cluster.png)

Panoptic groupe alors la vue selon cette propriété et ajoute un champ sous chaque cluster. Il suffit d'y entrer une valeur pour annoter toutes les images du cluster d'un coup : le cluster rejoint aussitôt le groupe correspondant. Dans l'exemple, le cluster des natures mortes a été annoté "fleurs" et les 140 images rejoignent le groupe "fleurs".

![](../images/v1/assigner-cluster-2.png)

### Annoter une partie d’un cluster, ou plusieurs parties de plusieurs clusters

Si les clusters proposés ne conviennent pas suffisamment pour annoter, il est possible de ne sélectionner qu’une partie des images qui s’affichent pour les annoter. Il suffit ici de reproduire l'annotation par lots décrite plus tôt, mais au sein d'un cluster.

!!! Important

    Il est possible de réaliser des sous-clusters (voir la documentation sur les [clusters](https://panopticorg.github.io/start/clusters/)). Ils fonctionnent comme les clusters et sont donc annotable de la même manière.

### Sauvegarder les clusters.

Par défaut, les clusters ne sont pas sauvegardés, car il s’agit de propositions informatiques d’associations d’images qu’un humain doit valider.

Si l’on souhaite conserver un cluster, il faut donc l'annoter, par exemple avec le bouton "Assigner à…" de la vue "Groupée" décrit plus haut. Les annotations s’enregistrent dans la propriété choisie, que vous pouvez retrouver dans la partie gauche de l’écran, sous la section propriété.

Pour conserver tous les clusters d'un coup, l'icône de disquette à côté de "All" les enregistre dans une nouvelle propriété "Clustering", avec ou sans la hiérarchie des sous-clusters (voir [Sauvegarder un clustering](/start/clusters/#sauvegarder-un-clustering)).

Vous pouvez ensuite renommer chaque élément de cette propriété pour donner du sens au clustering réalisé, en vous rendant dans la fenêtre de gestion des tags (voir la documentation sur la [gestion des propriétés de type Tag et Multitags](https://panopticorg.github.io/start/properties/)).

## Annoter des images similaires à une image

Lorsque l'on clique sur une image, s'ouvre une fenêtre contextuelle affichant l'image en grand. Les icônes en haut à gauche permettent d'afficher le panneau des propriétés de l'image (à gauche) et le panneau des images similaires (en bas).

![](../images/v1/similaires-1.png)

Vous pouvez annoter directement, par lots, ces différentes images. Plusieurs options ici : 

Vous pouvez au choix : sélectionner toutes les images affichées (coche à gauche de la barre des images similaires), ou bien sélectionner (ou désélectionner) certaines images pour affiner.

Vous pouvez ensuite cliquer sur l’icône "pot de peinture" à droite d'une propriété de l'image source pour donner la même valeur à toutes les images sélectionnées. Vous pouvez également utiliser la barre de sélection en haut à droite pour ouvrir le panneau affichant toutes les propriétés disponibles, et tagger les images sélectionnées comme bon vous semble (à l’identique de l’image originale, ou bien différemment).

![](../images/v1/similaires-2.png)

## Annoter des images similaires à un groupe d'images

Si vous avez déjà commencé à annoter votre corpus d’images, vous pouvez poursuivre l’annotation en cherchant des images similaires à un groupe d’images déjà annotées. Pour ce faire, il faut d’abord grouper les images en fonction d’une propriété (voir la documentation sur le [groupage d'images](https://panopticorg.github.io/start/filters/)). Pour chaque groupe, le menu des trois petits points propose alors l'option "Passer en vue recommandations".

![](../images/v1/reco-menu.png)

La vue "Recommandations" s'ouvre alors. En haut, une image proposée : il vous suffit de cliquer sur la coche verte ou la croix rouge, pour accepter que l’image proposée rejoigne le groupe associé, ou non (c’est-à-dire, pour valider ou non que l’image soit taggée avec l’annotation correspondante). En dessous sont affichées les prochaines recommandations, les images déjà présentes dans le groupe et la liste noire des images refusées.

![](../images/v1/reco-vue.png)

Si des filtres sont actifs dans l'onglet dans lequel vous travaillez, il est possible de choisir d’afficher des images similaires seulement présentes dans cet onglet, ou non, en activant ou désactivant le bouton "Filtrer" en haut à gauche de la vue.
