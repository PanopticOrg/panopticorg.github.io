# Créer des clusters pour identifier des tendances

## Objectif

Utiliser les outils de clustering de panoptic afin d'identifier différentes catégories d'images dans un corpus.

## Corpus

Prenons l'exemple d'un corpus d'environ 1200 photos d'oeuvres de l'Antiquité grecque et romaine autour des créatures mythologiques (gorgones, néréides, tritons, chevaux marins...) : mosaïques, vases, lampes, reliefs, statuettes, empreintes de gemmes, ainsi que des planches et photos anciennes en noir et blanc.

![Alt text](../images/v1/methode-corpus.png)

Ce corpus semble n'être pas facilement découpable en sous ensembles bien définis, comme en témoigne un aperçu dans la vue spatiale : on distingue les photos en couleur plutôt à gauche et les images en noir et blanc plutôt à droite, mais pas de groupes clairement séparés.

![Alt text](../images/v1/methode-carte.png)

## Comparer le clustering à la vue spatiale

Avant de se lancer dans un découpage fin, il est utile de faire quelques essais de clustering et de vérifier que le résultat est à peu près cohérent avec la répartition des images sur la carte. Les clusters et la carte sont calculés à partir des mêmes vecteurs : s'ils sont d'accord, c'est un bon signe que le découpage correspond à une organisation réelle du corpus.

Pour cela, on divise la vue (voir [Diviser la vue](/advanced/onglets/#diviser-la-vue)) avec :

- à gauche, la vue "Groupée", qui résume chaque cluster par une mosaïque d'images,
- à droite, la vue spatiale affichée sous forme de points (voir [La vue spatiale](/advanced/onglets/#la-vue-spatiale)).

Dès que des clusters sont créés, chaque point de la carte prend la couleur de son cluster, et la liste des clusters avec leur couleur s'affiche dans le panneau à droite de la carte. Un clustering cohérent avec la carte forme des zones de couleur bien distinctes, alors que des couleurs entremêlées signalent un découpage qui ne correspond pas à ce que montre la carte.

Voici trois essais réalisés sur ce corpus avec les vecteurs CLIP.

**Nombre de clusters automatique (-1).** Seuls 3 clusters sont produits : le premier regroupe 14 empreintes de gemmes presque identiques, le deuxième plus de 800 images, et le troisième, avec un score de 10000, rassemble les 394 images que l'algorithme n'a pu rattacher à aucun groupe. Sur la carte, les points jaunes de ce dernier sont dispersés partout : ce clustering ne dit presque rien de l'organisation du corpus.

![Alt text](../images/v1/methode-clusters-auto.png)

**30 clusters.** Les clusters sont très homogènes (une même mosaïque photographiée plusieurs fois, une même frise, une série d'empreintes de gemmes...), mais sur la carte les couleurs s'entremêlent : le découpage est plus fin que ce que la carte permet de distinguer, et il devient difficile d'avoir une vue d'ensemble du corpus.

![Alt text](../images/v1/methode-clusters-30.png)

**10 clusters.** Chaque couleur occupe une zone propre de la carte, et la plupart des clusters ont un contenu facile à identifier : gorgonéions dessinés ou en mosaïque, vases et coupes, mosaïques et sarcophages en couleur, reliefs en terre cuite, empreintes de gemmes sur fond bleu... C'est un bon point de départ pour la suite du travail.

![Alt text](../images/v1/methode-clusters-10.png)

!!! tip
    Le bon nombre de clusters dépend du corpus et il n'existe pas de valeur idéale : il vaut mieux faire plusieurs essais, en commençant par un petit nombre de clusters, puis l'augmenter tant que les couleurs restent bien séparées sur la carte. Le clustering n'étant pas déterministe, relancer une ou deux fois avec le même nombre permet aussi de vérifier que le résultat est stable.

## Clustering

Commencer par créer un clustering avec le nombre de clusters retenu à l'étape précédente. Le nombre de clusters automatique (-1) peut aussi donner de bons résultats, mais comme on l'a vu, il peut laisser une grande partie des images dans un cluster "bruit" au score très élevé. En vue "Grille", les clusters s'affichent les uns sous les autres, triés par score :

![Alt text](../images/v1/methode-clusters-grille.png)

On voit que pour les premiers clusters les résultats sont assez cohérents au niveau des types d'images regroupées ensemble : gorgonéions et créatures marines en mosaïque pour le premier, vases et coupes pour le second.
En revanche si l'on descend un peu et que l'on regarde les clusters avec un score plus élevé (donc avec une plus grande dispersion, c'est à dire une plus grande variété d'images) on constate effectivement un ensemble méritant d'être encore un peu séparé. Ici, le cluster 8 mélange des coupes, des lampes, des miroirs, des statuettes en bronze et des empreintes de gemmes :

![Alt text](../images/v1/methode-cluster-large.png)

## Clustering imbriqués

On peut venir ainsi reclusteriser les clusters que l'on considère comme trop larges, on peut parfois retenter -1, mais également demander parfois une séparation en un nombre spécifique de clusters quand il apparaît à l'oeil nu que deux ensemble se dégagent d'un même cluster, Dans l'exemple ci-dessous, le cluster 8 a d'abord été redivisé en 10 clusters, ce qui a bien séparé les coupes, les statuettes en bronze et les anses de vases. Le cluster entouré mélangeait encore des miroirs, des lampes et des candélabres : on l'a donc lui aussi divisé en trois.

![Alt text](../images/v1/methode-clusters-imbriques.png)

On peut ainsi continuer itérativement et continuer à découper nos clusters jusqu'à obtenir un niveau de détail satisfaisant.

On peut noter le cas intéressant de l'exemple ci-dessous, repris du clustering automatique vu plus haut : on a redemandé un découpage -1 au cluster "bruit" qui avait un score de 10000 (le score maximum, attribué au groupe des images que l'algorithme n'a pas su classer), et cela a à nouveau produit un groupe à 10000 de 240 images, c'est à dire que l'algorithme n'a pas été capable de découper de façon pertinente ce cluster là.

![Alt text](../images/v1/methode-clusters-bruit.png)

Dans ces cas là tout particulièrement il devient nécessaire de spécifier un nombre défini de clusters à produire pour forcer un découpage, ici 8 :

![Alt text](../images/v1/methode-clusters-forces.png)

## Sauvegarder les clusters

Une fois que l'on est satisfait on peut venir sauvegarder le résultat du cluster pour en faire une propriété persistée et par laquelle on va pouvoir venir manipuler les images. Le plus simple est de cliquer sur l'icône de disquette à côté de "All" puis sur "Avec la hiérarchie" : tous les clusters deviennent des tags d'une nouvelle propriété "Clustering", et les clusters imbriqués deviennent des tags enfants de leur cluster d'origine (voir [Sauvegarder un clustering](/start/clusters/#sauvegarder-un-clustering)). Il est aussi possible de passer en vue "Groupée" et d'utiliser le bouton "Assigner à…" sous chaque cluster pour n'en enregistrer que certains (voir [Annoter un cluster en entier](/start/annotate/#annoter-un-cluster-en-entier)). 

## Demander des recommandations

Une fois que la propriété est créée on peut grouper les images par cette propriété et venir demander des recommandations à panoptic pour voir si certains groupes pourraient être complétés (voir [Les recommandations](/start/reco/)).
Ici par exemple on observe un cluster assez large, "Clustering_10.1", contenant des vases et des coupes, en métal ou en céramique. On peut alors soit demander des recommandations générales comme sur l'image ci-dessous, ce qui va nous proposer de nouvelles coupes, lampes et vases, que l'on valide ou refuse une à une, soit il est peut être pertinent de redécouper ce groupe afin d'être plus précis dans son contenu.

![Alt text](../images/v1/methode-recommandations.png)

## Renommer ses clusters

Une fois ce travail réalisé, il est possible d'ouvrir la propriété utilisée à l'étape de sauvegarde des clusters dans la modale des tags (voir [La fenêtre de gestion des tags](/advanced/tagsmodal/)). La vue arbre permet de retrouver la hiérarchie des clusters imbriqués :

![Alt text](../images/v1/methode-tags-arbre.png)

On peut alors revenir sur les clusters un à un pour les renommer et leur donner des noms pertinents en fonction de leur contenu, ou encore venir fusionner certains tags au cas où on aurait trop découpé certains ensembles au moment du clustering. Pour ce faire, on sélectionne les tags en maintenant la touche CTRL, puis on clique sur "Merge Tags". Dans l'exemple ci-dessous, les coupes isolées dans "Clustering_10.8.0" peuvent rejoindre les vases et coupes de "Clustering_10.1" :

![Alt text](../images/v1/methode-tags-fusion.png)