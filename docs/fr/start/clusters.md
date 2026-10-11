# Les Clusters

Les clusters sont une notion particulièrement importante dans le fonctionnement de Panoptic.
Une fois les vecteurs calculés, les images peuvent être regroupées automatiquement en **clusters**. Contrairement aux groupes créés avec des propriétés, les clusters sont paramétrables, peuvent être générés avec différents algorithmes, et ne sont pas déterministes (un même clustering peut produire des résultats légèrement différents selon les exécutions).

## Créer des clusters

Une fois le projet lancé et les plugins chargés, cliquer sur les trois petits points à côté de "All" (ou à côté du nom d'un groupe) puis sur "Créer des clusters". Cette option est aussi accessible directement par l'icône qui apparaît au survol du nom du groupe.

![Alt text](../images/v1/groupe-menu.png)

Une petite fenêtre de paramètres s'ouvre. Cliquez sur "Lancer" : cela devrait séparer vos images en 10 groupes distincts par similarité comme sur l'image ci dessous:

![Alt text](../images/v1/clusters.png)

### Les paramètres

Avant de lancer le calcul, il est possible de choisir le nombre de clusters que l'on souhaite produire en modifiant la valeur de nb_clusters.

![Alt text](../images/v1/clusters-parametres.png)

!!! Info
    Le paramètre vec_type permet de choisir les vecteurs à utiliser, si plusieurs types de vecteurs ont été calculés pour le projet (voir [Choisir son modèle](/advanced/models/)).

!!! Nombre de clusters automatique
    Il est également possible de demander un nombre automatique de clusters à produire en entrant `-1` dans la valeur nb_clusters, mais il est à noter que cela prendra plus de temps à calculer et que le résultat sera vraiment variable d'un corpus à l'autre.

### Les scores

Les clusters produits possèdent chacun un score affiché en couleur à côté de leur nom, ces scores sont un indicateur de la pertinence du cluster, c'est à dire à quel point les images au sein de ce dernier sont proches les unes des autres. Plus le score est faible et plus le cluster est considéré comme **cohérent.** Ce score est là pour donner une *idée générale* et peut **varier d'un corpus à l'autre**. Autrement dit, si un score de 15 peut donner un cluster avec des images presque visuellement identiques dans certains corpus, cela sera peut être plus disparate dans d'autres. Cela dépend de la diversité et du nombre d'images présentes dans ce dernier.

### La vue "Groupée"

Pour avoir une vue d'ensemble des clusters, il est conseillé de passer en vue "Groupée" (menu des vues, en haut à gauche des images, voir [Les onglets](/advanced/onglets/)). Chaque cluster y est résumé par une mosaïque de quelques images, avec son score et son nombre d'images. Les icônes en haut à gauche de la vue permettent de choisir entre une image unique ou une mosaïque plus ou moins grande pour chaque cluster.

![Alt text](../images/v1/vue-groupee.png)

## Imbriquer des clusters

Une fonctionnalité importante de panoptic et la possibilité d'imbriquer des clusters. En effet, le postulat suivi ici est de dire que les modèles d'apprentissage automatique ne produiront jamais de clustering parfait et que celui ci doit / peut être retravaillé par la personne utilisant panoptic. De fait il est possible de rediviser un cluster en utilisant de nouveau "Créer des clusters" depuis le menu de ce cluster afin d'affiner le regroupement des images. 

Ce processus peut être d'ailleurs répété indéfiniment (enfin tant qu'il reste des images à séparer).

Pour retirer les clusters et revenir à l'affichage initial, cliquez sur la croix qui apparaît à côté de "All".

## Sauvegarder un clustering

Le processus de clustering est avant tout un outil d'exploration est n'est pas sauvegardé automatiquement dans panoptic. Si l'on veut persister le travail effectué grâce à cet outil, il faut l'enregistrer dans une propriété.

### Enregistrer tous les clusters d'un coup

L'icône de disquette qui apparaît à côté de "All" (ou à côté d'un cluster qui a été redivisé) permet d'enregistrer en une seule fois tous les clusters affichés dans une nouvelle propriété de type multi tags nommée "Clustering". Chaque cluster devient un tag, nommé d'après sa position dans le clustering : par exemple "Clustering_8.0" pour le premier des 8 clusters, puis "Clustering_8.0.1" pour le deuxième sous-cluster de celui-ci.

![Alt text](../images/v1/clusters-sauvegarde.png)

Trois modes d'enregistrement sont proposés, qui ne diffèrent que lorsque des clusters ont été imbriqués:

- **Avec la hiérarchie**: chaque cluster devient un tag et les sous-clusters deviennent des tags enfants du tag de leur cluster. Chaque image reçoit le tag du plus petit cluster dans lequel elle se trouve, et hérite ainsi des tags parents (voir [Les tags](/advanced/tags/)).
- **Sans la hiérarchie**: chaque cluster devient un tag, sans aucun lien de parenté entre les tags. Chaque image reçoit le tag de son cluster ainsi que les tags de tous les clusters qui le contiennent.
- **Uniquement les clusters feuilles**: seuls les clusters qui n'ont pas été redivisés deviennent des tags, les niveaux intermédiaires sont ignorés.

Voici par exemple le résultat d'un enregistrement avec la hiérarchie, vu dans la vue arbre de la fenêtre des tags : le premier cluster a été redivisé en trois, et ses trois sous-clusters sont devenus ses tags enfants.

![Alt text](../images/v1/clusters-sauvegarde-arbre.png)

Il ne reste ensuite plus qu'à renommer les tags pour leur donner des noms pertinents (voir [La fenêtre de gestion des tags](/advanced/tagsmodal/)).

### Annoter les clusters un par un

Si l'on préfère n'enregistrer que certains clusters, ou les ranger directement dans une propriété existante, on peut utiliser le bouton "Assigner à…" de la vue "Groupée", qui permet de donner une valeur à tout un cluster en une seule fois (voir [Annoter un cluster en entier](/start/annotate/#annoter-un-cluster-en-entier)).

![Alt text](../images/v1/assigner-cluster-2.png)

## Différentes façons de clusteriser

La méthode principale présentée jusqu'ici est celle par défaut "PanopticML.compute_clusters" mais il existe dans le plugin de similarité d'autres façons de créer des clusters, et d'autres plugins pourront également proposer d'autres façons. Celles disponibles par défaut dans le plugin de similarité sont les suivantes:

- compute_clusters: version par défaut qui utilise l'algorithme KMeans et regroupe les images en fonction d'un nombre de clusters demandés, pratique pour itérer rapidement et effectuer de "grosses coupes" dans un corpus.
- find_duplicates: créé des groupes en assurant un minimum de seuil de similarité entre les images de ce groupes, cela peut être pratique pour identifier les doublons ou doublons proches dans un corpus. Le seuil de similarité peut être modifié pour être plus ou moins permissif.
- cluster_by_tags: *experimental*, prend en entrée une propriété de type tags ou multitags et essaie de ratacher chaque image au tag dont elle est le plus proche.

Cette méthode peut être choisie depuis le champ déroulant en haut de la fenêtre des paramètres de clustering: 

![Alt text](../images/v1/clusters-fonctions.png)

## Pour aller plus loin

Pour des exemples concrets d'utilisation voir [un exemple de méthodologie utilisant le clustering](/method/clusters)
