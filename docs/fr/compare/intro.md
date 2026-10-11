# Comparaison de modèles

Le plugin de similarité de panoptic propose plusieurs modèles pour calculer les vecteurs des images (voir [Choisir son modèle](/advanced/models/)). Chacun produit une représentation différente des images, ce qui change le résultat de tous les outils de similarité : la carte de la vue spatiale, les clusters, la recherche par texte, les images similaires ou encore la détection de doublons.

Cette section compare ces modèles sur un même petit corpus, afin de donner des repères pour choisir. Elle ne remplace pas un test sur son propre corpus : un modèle peut très bien se comporter sur des peintures et beaucoup moins bien sur des photos de presse ou des captures d'écran.

## Le protocole

### Le corpus

Le corpus de test est composé de 1200 peintures issues de [WikiArt](https://www.wikiart.org/), à raison de 100 oeuvres pour chacun des 12 artistes suivants : Albrecht Dürer, Rembrandt, Ivan Aïvazovski, Ivan Chichkine, Gustave Doré, Claude Monet, Camille Pissarro, Edgar Degas, Mary Cassatt, Paul Cézanne, Paul Gauguin et Vincent van Gogh.

Chaque image a été annotée en important un fichier CSV (voir [Importer des Propriétés](/start/propsimport/)) avec trois propriétés de type tag : l'artiste, le genre (paysage, portrait, scène de genre, scène religieuse...) et le mouvement artistique (impressionnisme, romantisme, baroque...). Ces propriétés servent de point de repère : un modèle qui place côte à côte des oeuvres du même artiste, du même genre ou du même mouvement produit une organisation plus facile à interpréter. Il ne s'agit toutefois que d'une approximation, deux images peuvent être très proches sans partager aucune de ces propriétés.

Un second corpus, décrit dans la page [Doublons proches](/compare/doublons/), a été construit pour tester la détection de doublons.

### Les modèles comparés

Les 9 modèles proposés par défaut dans le plugin de similarité ont été comparés :

| Modèle | Identifiant | Taille des vecteurs | Recherche par texte |
| --- | --- | --- | --- |
| CLIP (modèle par défaut) | openai/clip-vit-base-patch32 | 512 | oui |
| MobileNet | google/mobilenet_v2_1.0_224 | 1280 | non |
| MobileCLIP2-S2 | apple/MobileCLIP2-S2 | 512 | oui |
| MobileCLIP2-L-14 | apple/MobileCLIP2-L-14 | 768 | oui |
| SigLIP2 | google/siglip2-so400m-patch16-naflex | 1152 | oui |
| EmbeddingGemma 2 | google/embeddinggemma-2 | 768 | oui |
| DINOv2 | facebook/dinov2-base | 768 | non |
| DINOv3 | phunghuy159/dinov3 | 1024 | non |
| C-RADIOv4 | nvidia/C-RADIOv4-H | 2560 | non |

### La machine

Les mesures ont été réalisées sur un ordinateur portable équipé d'un processeur Intel Core Ultra 7 255HX (20 coeurs), de 32 Go de mémoire vive et d'une carte graphique NVidia RTX PRO 4000 (16 Go).

## Tableau récapitulatif

Le détail de chaque mesure est expliqué dans les pages suivantes : [Temps de calcul](/compare/temps/), [Spatialisation](/compare/spatialisation/), [Clusters](/compare/clusters/), [Recherche par texte](/compare/texte/) et [Doublons proches](/compare/doublons/).

| Modèle | Temps pour 1000 images (processeur) | Temps pour 1000 images (carte graphique) | Carte : voisins du même artiste | Clusters : accord avec les artistes | Recherche par texte (anglais / français) | Doublons : copie retrouvée en premier |
| --- | --- | --- | --- | --- | --- | --- |
| CLIP | 20 s | 1 s | 60 % | 0,49 | 68 % / 49 % | 99 % |
| MobileNet | 21 s | 3 s | 44 % | 0,38 | non | 90 % |
| MobileCLIP2-S2 | 1 min 43 | 5 s | 54 % | 0,44 | 63 % / 61 % | 98 % |
| MobileCLIP2-L-14 | 4 min 29 | 19 s | 63 % | 0,50 | non testé | 96 % |
| SigLIP2 | 6 min 10 | 10 s | 75 % | 0,60 | 73 % / 70 % | 91 % |
| EmbeddingGemma 2 | 38 min | 58 s | 73 % | 0,56 | 65 % / 61 % | 85 % |
| DINOv2 | 1 min 18 | 2 s | 46 % | 0,34 | non | 94 % |
| DINOv3 | 3 min 23 | 4 s | 54 % | 0,48 | non | 100 % |
| C-RADIOv4 | 38 min | 2 min 26 | 71 % | 0,58 | non | 98 % |

La recherche par texte a été évaluée sur un corpus plus large de 10 000 peintures, avec des requêtes portant sur les artistes, les styles, les genres, les couleurs et le contenu des images (voir [Recherche par texte](/compare/texte/)). MobileCLIP2-L-14 n'a pas été inclus dans ce test.

## Quel modèle choisir ?

- **Pour commencer, ou sur une machine modeste** : CLIP, le modèle par défaut, reste un très bon compromis. C'est le plus rapide de tous, ses cartes et ses clusters sont corrects, et il permet la recherche par texte, de préférence en anglais.
- **Pour obtenir les cartes, les clusters et la recherche par texte les plus pertinents** : SigLIP2 est le modèle qui regroupe le mieux les oeuvres d'un même artiste ou d'un même mouvement, et celui qui donne les meilleurs résultats en recherche par texte, en anglais comme en français, à condition d'écrire les requêtes en minuscules (voir [Recherche par texte](/compare/texte/)). Son temps de calcul reste raisonnable avec une carte graphique (environ 6 minutes pour 1000 images sans carte graphique). C-RADIOv4 et EmbeddingGemma 2 donnent des cartes et des clusters proches, mais sont beaucoup plus lents.
- **Pour chercher par texte en français sur une machine modeste** : MobileCLIP2-S2 est rapide et se comporte presque aussi bien en français qu'en anglais, contrairement à CLIP qui est à éviter pour les requêtes en français.
- **Pour chercher par des descriptions complexes** (plusieurs personnages, une action, des attributs combinés) : EmbeddingGemma 2 s'en sort un peu mieux que les autres, même si aucun modèle ne réussit vraiment ce type de requête.
- **Pour trouver des doublons** : DINOv3 retrouve toutes les copies du corpus de test, y compris les images tournées, et c'est celui qui en regroupe le plus avec le seuil de similarité par défaut.
- **C-RADIOv4 et EmbeddingGemma 2** sont à réserver aux machines équipées d'une carte graphique : sans elle, il faut compter près de 40 minutes pour 1000 images.
- **MobileNet** n'a plus beaucoup d'intérêt : il n'est pas plus rapide que CLIP dans nos mesures et produit les cartes et les clusters les moins structurés.

!!! note

    Il est tout à fait possible de calculer les vecteurs de plusieurs modèles dans un même projet et de passer de l'un à l'autre selon l'outil utilisé, par exemple CLIP pour la recherche par texte et DINOv3 pour la recherche de doublons (voir [Choisir son modèle](/advanced/models/)).

## Les limites de cette comparaison

Ces résultats portent sur des corpus composés uniquement de peintures, et en grande partie sur des métadonnées qui ne décrivent qu'une partie de ce que représentent les images. Ils donnent des tendances plutôt qu'un classement définitif : sur un autre corpus, l'ordre des modèles peut changer. Les temps de calcul dépendent quant à eux fortement de la machine utilisée.
