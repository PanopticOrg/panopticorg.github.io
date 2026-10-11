# Les Propriétés

Pour donner du sens aux images étudiées dans l’interface de Panoptic, cela se fait en **créant** et **définissant** un ensemble de PROPRIÉTÉS. C’est à partir des propriétés créées que vous pouvez annoter les images. Ces propriétés sont de plusieurs types : 

- MultiTags, 
- Tag, 
- Texte, 
- Nombre, 
- Date,
- Color (couleur),
- URL, 
- Checkbox (case à cocher).

Une fois les propriétés créées, vous pouvez associer des annotations à chaque image séparément, ou bien à des lots d’images, en lien avec une propriété particulière, ou bien avec plusieurs propriétés. Les propriétés peuvent être créées au fur et à mesure, et pas nécessairement définies en amont.

## Créer et afficher une propriété

Pour annoter vos images, il faut au préalable créer au moins une propriété, qui contiendra des annotations de types spécifiques (tag, date, texte, nombre...).
    
Pour créer une propriété (par exemple de type "MultiTags") :
     
- À gauche, dans la section "Propriétés", cliquez sur le "+" ("Nouvelle propriété").

![image](../images/v1/creer-prop-1.png)

-  Nommez la propriété, choisissez son type dans la liste "Type de propriété" et choisissez s'il s'agit d'une propriété d'image ou d'instance (menu "Propriété d'image" à gauche du nom). En survolant chaque type, une courte description s'affiche. Faites "Confirmer".

![image](../images/v1/creer-prop-2.png)

- La propriété créée s'affiche directement sous toutes les images. Pour l'afficher ou la masquer, il suffit de cliquer sur son nom dans la section "Propriétés" : les propriétés affichées sont surlignées en bleu.

![image](../images/v1/creer-prop-3.png)

!!! Important

    Il n'est pas nécessaire de définir en amont les propriétés dont vous aurez besoin au cours du travail. Celles-ci peuvent être créées au fur et à mesure.

Au survol d'une propriété, plusieurs icônes apparaissent à droite de son nom. Elles permettent, de gauche à droite, d'afficher la liste de ses tags (pour les propriétés de type Tag et MultiTags), d'ouvrir la fenêtre de gestion des tags, de filtrer, de trier ou de grouper les images selon cette propriété. Les trois petits points permettent de renommer ou de supprimer la propriété.

![image](../images/v1/propriete-survol.png)

## Organiser les propriétés en groupes

Lorsque le nombre de propriétés augmente, il est possible de les ranger dans des groupes. Cliquez sur l'icône de dossier à droite du titre "Propriétés" ("Nouveau Groupe") : un groupe apparaît en haut de la liste. Au survol du groupe, les trois petits points permettent de le renommer ou de le supprimer, et le "+" d'y créer directement une nouvelle propriété. Pour déplacer une propriété existante dans un groupe, il suffit de la glisser avec la souris sur le groupe souhaité.

![image](../images/v1/groupes-proprietes.png)

L'icône d'oeil à droite du nom d'un groupe permet d'afficher ou de masquer d'un coup toutes les propriétés qu'il contient.

## Propriétés d'images, propriétés d'instances

Un point qui peut être compliqué à décider est le choix entre **propriétés d'images** et **propriétés d'instances**. Pour comprendre la différence entre les notions d'**images** et d'**instances d'images**, vous pouvez vous référer au [glossaire](https://panopticorg.github.io/concepts/).

- Si vous choisissez l'option **propriété d'images**, vous annoterez, pour la propriété créée, toutes les instances d'une même image. 
- Si vous choisissez l'option **propriété d'instance**, vous annoterez une seule instance de l'image.

Par exemple, vous travaillez avec des tweets qui contiennent des images. Si 50 tweets différents mobilisent une même image :

- Choisir l'option **propriété d'images** vous permettra d'annoter les 50 tweets d'un coup, qui mobilisent une même image : c'est pertinent si vous souhaitez décrire l'image en tant que telle, mais ça ne l'est pas si vous souhaitez annoter le contexte de mobilisation de l'image.
- Choisir l'option **propriété d'instance** vous permettra d'annoter les tweets un par un : c'est pertinent si vous souhaitez décrire le contexte de mobilisation de l'image, mais ça ne l'est pas si vous voulez annoter l'image en tant que telle.

## Relations entre propriétés

Il est possible de définir des relations hiérarchiques (parent-enfant) entre annotations, pour les propriétés de type **Tag** et **MultiTags**. Ces propriétés sont en effet spécifiques et peuvent être gérées dans un espace dédié. Cet espace s'ouvre depuis le volet des propriétés, situé à gauche de l'écran, en survolant la propriété puis en cliquant sur l'icône d'agrandissement ("Ouvrir modal des tags").

![image](../images/v1/propriete-survol.png)

!!! Important

    Dans cet espace de gestion des tags et de leurs relations, deux vues sur ces relations sont disponibles en fonction des besoins : la vue "liste" et la vue "arbre". On passe de l'une à l'autre avec les icônes en haut à gauche de la fenêtre. Les onglets à droite de ces icônes permettent de passer d'une propriété à une autre.

### Vue "liste" des propriétés Tag et Multitags

Dans la vue "liste", lorsque vous sélectionnez un tag, cela affiche ses différentes relations : parents, frères (mêmes parents), enfants, ainsi que les images associées à droite. Dans l'exemple, le tag "paysages" a pour enfants "forêts" et "marines" : il regroupe donc les images de ces deux tags.

![image](../images/v1/tags-liste.png)

Pour créer une relation, il suffit de glisser un tag de la colonne "Tous les tags" vers la colonne "Tags parents" ou "Tags enfants" du tag sélectionné.

Dans cet espace de gestion des tags, vous pouvez renommer vos différents tags, pour les améliorer si besoin, ou encore les fusionner entre eux, si vous repérez des doublons par exemple. Pour les fusionner, sélectionnez plusieurs tags (en maintenant la touche ctrl) et faites "Merge Tags".

![image](../images/v1/tags-fusion.png)

### Vue "arbre" des propriétés Tag et Multitags

La vue "arbre" montre d'un coup d'oeil les relations parents-enfants existantes, de gauche (parents) à droite (enfants). Dans l'exemple : paysages/marines/bateaux ; paysages/forêts ; animaux/chevaux. Cliquer sur un tag le sélectionne et affiche ses images à droite de la fenêtre.

![image](../images/v1/tags-arbre.png)

## Les Propriétés Panoptic

Les propriétés de la section "MÉTADONNÉES" sont des propriétés non modifiables. Elles sont calculées par le logiciel lors de l’import des images, et vous fournissent quelques métriques : un identifiant unique pour chaque instance ("id"), une signature propre à chaque image, pour repérer les doublons parfaits ("sha1"), l'identifiant du fichier ("file_id"), le dossier d’origine sur votre ordinateur ("folder"), le nom du fichier ("name"), son chemin absolu ("path"), son format ("format"), ses dimensions ("width" et "height"), et enfin sa date de création ("created_at").
