# Temps de calcul

Le calcul des vecteurs est l'étape la plus longue de l'utilisation des outils de similarité : il n'est fait qu'une seule fois par modèle, mais il peut prendre de quelques secondes à plusieurs heures selon le modèle, le nombre d'images et la machine.

## La mesure

Pour chaque modèle, un type de vecteurs a été créé dans les paramètres du projet (voir [Choisir son modèle](/advanced/models/)) et le temps de calcul a été relevé :

- avec la carte graphique, sur les 1200 images du corpus,
- sans carte graphique (uniquement avec le processeur), sur un échantillon de 200 images du même corpus.

Le temps mesuré ne compte que le calcul des vecteurs. Il faut y ajouter, la première fois qu'un modèle est utilisé, le temps de le télécharger, puis à chaque calcul quelques secondes pour le charger en mémoire.

![Alt text](../images/v1/compare/vecteurs-modeles.png)

## Les résultats

| Modèle | Carte graphique (images par seconde) | Processeur (images par seconde) | 10 000 images avec carte graphique | 10 000 images sans carte graphique |
| --- | --- | --- | --- | --- |
| CLIP | 800 | 50 | 13 s | 3 min 20 |
| MobileNet | 300 | 49 | 33 s | 3 min 25 |
| MobileCLIP2-S2 | 222 | 9,7 | 45 s | 17 min |
| DINOv2 | 632 | 12,9 | 16 s | 13 min |
| DINOv3 | 273 | 4,9 | 37 s | 34 min |
| MobileCLIP2-L-14 | 54 | 3,7 | 3 min | 45 min |
| SigLIP2 | 101 | 2,7 | 1 min 40 | 1 h 02 |
| EmbeddingGemma 2 | 17 | 0,44 | 10 min | 6 h 20 |
| C-RADIOv4 | 6,8 | 0,44 | 25 min | 6 h 20 |

Les temps pour 10 000 images sont des estimations calculées à partir des mesures.

On distingue ainsi trois familles de modèles :

- **les modèles légers** (CLIP, MobileNet, DINOv2, MobileCLIP2-S2) restent utilisables sans carte graphique, même sur plusieurs dizaines de milliers d'images,
- **les modèles intermédiaires** (DINOv3, MobileCLIP2-L-14, SigLIP2) demandent de l'ordre d'une heure pour 10 000 images sans carte graphique, ce qui reste envisageable en laissant tourner le calcul,
- **les modèles lourds** (EmbeddingGemma 2, C-RADIOv4) sont 100 fois plus lents que CLIP sans carte graphique et ne sont vraiment utilisables qu'avec elle.

!!! note

    Avec les modèles les plus rapides, ce n'est plus le modèle qui limite la vitesse mais la lecture et le redimensionnement des images. C'est pourquoi MobileNet, pourtant présenté comme un modèle très léger, n'est pas plus rapide que CLIP sans carte graphique.

!!! note "Mémoire"

    Les modèles les plus lourds occupent aussi davantage de mémoire. Sur une carte graphique de 16 Go déjà partiellement utilisée, le calcul des vecteurs de C-RADIOv4 a échoué faute de mémoire alors que plusieurs autres modèles étaient déjà chargés. Relancer Panoptic avant le calcul libère cette mémoire.
