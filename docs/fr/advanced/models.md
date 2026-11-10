# Choisir son modèle

Pour des usages plus avancés, il est possible de comparer des modèles de vectorisation d'images entre eux. Celui utilisé de base par le plugin de similarité de panoptic est le modèle CLIP d'OpenAI (quand ils étaient encore Open). 
Mais il existe d'autres modèles qui proposeront une représentation vectorielle différente et qui peuvent être plus ou moins efficace en fonction des jeux de données. Certains d'entre eux sont directement intégrés au plugin de similarité:

- Mobilenet (google/mobilenet_v2_1.0_224): modèle aux performances moyennes mais étant beaucoup plus léger en terme de calcul, bien dans le cas d'utilisation sur une machine ayant peu de puissance de calcul cpu, ne permet pas de similarité texte / image.
- CLIP (openai/clip-vit-base-patch32): modèle par défaut de panoptic, bonnes performances et tourne relativement vite sur la plupart des machines, permet de faire de la similarité texte / image
- SIGLIP2 (google/siglip2-so400m-patch16-naflex): modèle plus lourd que CLIP, mais obtenant de meilleures performances en similarité texte / image, les vecteurs seront beaucoup plus long à calculer sur une machine moyenne. Une carte graphique NVidia est recommandée.
- DINOv2 (facebook/dinov2-base): modèle plus lourd que CLIP, censé avoir de meilleures performances sur la similarité visuelle, ne permet pas de faire de la similarité texte / image
- DINOv3 (phunghuy159/dinov3): successeur de DINOv2, avec de meilleures caractéristiques visuelles, ne permet pas de faire de la similarité texte / image
- C-RADIOv4 (nvidia/C-RADIOv4-H): modèle de vision lourd, carte graphique recommandée, ne permet pas de faire de la similarité texte / image
- MobileCLIP2 (apple/MobileCLIP2-S2 et apple/MobileCLIP2-L-14): modèles proches de CLIP mais plus rapides, permettent de faire de la similarité texte / image

## Créer de nouveaux vecteurs

Afin de pouvoir tester ces différents modèles, il faut générer les vecteurs associés à ce modèle, on se rend donc dans les paramètres du projet, en cliquant sur la petite roue dentée à côté du nom du projet:

- Puis on se rend dans Vecteurs > Ajouter un type de vecteur.
- On choisit le nom du modèle que l'on souhaite utiliser dans le champ "model", par exemple google/siglip2-so400m-patch16-naflex
- On confirme en appuyant sur Créer et le calcul devrait se lancer en quelques secondes. Sa progression s'affiche en haut de l'écran, à droite du nom du projet.

![Alt text](../images/v1/parametres-vecteurs.webp)

!!! note

    Il est possible d'également cocher l'option "greyscale" avant d'appuyer sur "Créer" si l'on souhaite ignorer la couleur des images, cela peut être utile par exemple dans un corpus possédant des images en noir et blanc et d'autres en couleurs si jamais on ne souhaitait pas que la couleur soit un critère déterminant par rapport à ce qui est représenté à l'image.

!!! note

    Certains modèles proposent des options supplémentaires, qui n'apparaissent que lorsqu'ils sont choisis :

    - SIGLIP2 : `keep_ratio` (coché par défaut) analyse les images avec leurs proportions d'origine au lieu de les déformer en carré. Cela ne coûte rien de plus en temps de calcul, sauf sur Mac Apple Silicon où le calcul peut être 2 à 3 fois plus lent.
    - DINOv3 : `high_resolution` analyse les images à 768 px au lieu de 256 px, pour mieux distinguer des images qui ne diffèrent que par leurs détails (pages manuscrites par exemple). Le calcul est nettement plus long.

    Voir par exemple [Trouver des doublons entre deux dossiers](../method/doublons_dossiers.md).

!!! note

    Décocher "Calculer maintenant" permet de créer le type de vecteurs sans lancer le calcul tout de suite. Dans ce cas, ou si pour une raison quelconque le calcul des vecteurs venait à être interrompu, il est possible de le relancer depuis la liste "Vecteurs disponibles" en cliquant sur "calculer" dans la colonne "Généré". Cette colonne indique le nombre d'images pour lesquelles les vecteurs ont été calculés.

La première fois qu'un modèle est utilisé, il est téléchargé depuis [Hugging Face](https://huggingface.co/), ce qui peut prendre un peu de temps selon sa taille.

## Utiliser les vecteurs

Une fois généré, les nouveaux vecteurs ne sont pas utilisés par défaut, comme les autres vecteurs (CLIP par exemple) restent disponibles il faut choisir lorsque l'on execute une action quels vecteurs l'on souhaite utiliser.

Ainsi dans n'importe quelle action de similarité panoptic, clustering, similarité visuelle, similarité textuelle, recommandation de groupe, carte de la vue spatiale, il est toujours possible de préciser quels vecteurs utiliser: 

- Lors de l'execution d'une fonction on appuie sur vec_type et on vient choisir les vecteurs que l'on vient de générer. Dans l'exemple ci-dessous, on choisit les vecteurs utilisés pour chercher les images similaires dans la fenêtre d'une image:

![Alt text](../images/v1/choix-vecteurs.webp)
