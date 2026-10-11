# Clusters

Les clusters regroupent automatiquement les images à partir de leurs vecteurs (voir [Les Clusters](/start/clusters/)). Comme pour la carte, le résultat dépend du modèle utilisé : deux modèles différents ne découpent pas le corpus de la même façon.

## La mesure

Pour chaque modèle, les 1200 images ont été réparties en 12 clusters avec la fonction par défaut "PanopticML.compute_clusters", soit autant de clusters que d'artistes dans le corpus. Les clusters ont ensuite été comparés aux propriétés artiste, genre et mouvement à l'aide d'un score d'accord (l'information mutuelle normalisée) :

- un score de 0 signifie que les clusters n'ont aucun lien avec la propriété,
- un score de 1 signifie que chaque cluster correspond exactement à une valeur de la propriété.

Le clustering n'étant pas déterministe, le score retenu est la moyenne de 5 clusterings successifs.

## Les résultats

| Modèle | Accord avec les artistes | Accord avec les genres | Accord avec les mouvements |
| --- | --- | --- | --- |
| CLIP | 0,49 | 0,45 | 0,37 |
| MobileNet | 0,38 | 0,38 | 0,27 |
| MobileCLIP2-S2 | 0,44 | 0,49 | 0,32 |
| MobileCLIP2-L-14 | 0,50 | 0,49 | 0,37 |
| SigLIP2 | 0,60 | 0,47 | 0,46 |
| EmbeddingGemma 2 | 0,56 | 0,41 | 0,40 |
| DINOv2 | 0,34 | 0,42 | 0,23 |
| DINOv3 | 0,48 | 0,46 | 0,37 |
| C-RADIOv4 | 0,58 | 0,49 | 0,46 |

Ces résultats rejoignent ceux de la [spatialisation](/compare/spatialisation/) : les modèles qui produisent les cartes les mieux organisées produisent aussi les clusters les plus cohérents. Aucun modèle n'atteint toutefois un découpage parfait par artiste, ce qui est attendu : un clustering regroupe ce qui se ressemble, et deux paysages enneigés de Monet et de Pissarro se ressemblent souvent davantage que deux oeuvres très différentes d'un même peintre.

Voici les 12 clusters obtenus avec chaque modèle, en vue "Groupée" :

=== "CLIP"

    ![Alt text](../images/v1/compare/clusters-clip.png)

=== "MobileNet"

    ![Alt text](../images/v1/compare/clusters-mobilenet.png)

=== "MobileCLIP2-S2"

    ![Alt text](../images/v1/compare/clusters-mobileclip2-s2.png)

=== "MobileCLIP2-L-14"

    ![Alt text](../images/v1/compare/clusters-mobileclip2-l14.png)

=== "SigLIP2"

    ![Alt text](../images/v1/compare/clusters-siglip2.png)

=== "EmbeddingGemma 2"

    ![Alt text](../images/v1/compare/clusters-gemma2.png)

=== "DINOv2"

    ![Alt text](../images/v1/compare/clusters-dinov2.png)

=== "DINOv3"

    ![Alt text](../images/v1/compare/clusters-dinov3.png)

=== "C-RADIOv4"

    ![Alt text](../images/v1/compare/clusters-radio.png)

## Ce que l'on observe

- **SigLIP2 et C-RADIOv4** produisent des clusters à la fois homogènes et faciles à nommer : marines dans la tempête, marines au coucher du soleil, danseuses de Degas, portraits de Van Gogh, scènes religieuses de Rembrandt, bouquets de fleurs...
- **CLIP** produit des clusters cohérents par sujet (portraits, champs, bouquets, dessins...), en mélangeant plus volontiers les artistes à l'intérieur d'un même sujet.
- **DINOv2** regroupe avant tout par motif (portraits, bateaux, forêts, falaises, intérieurs), quelle que soit la technique : un même cluster peut contenir des dessins en noir et blanc et des peintures en couleurs.
- **MobileNet** produit des clusters plus difficiles à nommer, qui mélangent souvent les sujets et les artistes.

!!! note "Les scores des clusters"

    Le score affiché à côté de chaque cluster (voir [Les scores](/start/clusters/#les-scores)) dépend du modèle et ne peut pas être comparé d'un modèle à l'autre. Avec MobileNet par exemple, dont les vecteurs ne sont pas normalisés, les scores atteignent plusieurs dizaines de milliers, alors qu'ils sont de l'ordre de quelques dizaines avec les autres modèles.
