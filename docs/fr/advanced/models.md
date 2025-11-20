# Choisir son modèle

Pour des usages plus avancés, il est possible de comparer des modèles de vectorisation d'images entre eux. Celui utilisé de base par le plugin de similarité de panoptic est le modèle CLIP d'OpenAI (quand ils étaient encore Open). 
Mais il existe d'autres modèles qui proposeront une représentation vectorielle différente et qui peuvent être plus ou moins efficace en fonction des jeux de données. Certains d'entre eux sont directement intégrés au plugin de similarité:

- Mobilenet: modèle aux performances moyennes mais étant beaucoup plus léger en terme de calcul, bien dans le cas d'utilisation sur une machine ayant peu de puissance de calcul cpu, ne permet pas de similarité texte / image.
- CLIP: modèle par défaut de panoptic, bonnes performances et tourne relativement vite sur la plupart des machines, permet de faire de la similarité texte / image
- SIGLIP: modèle plus lourd que CLIP, mais obtenant de meilleures performances en similarité texte / image, les vecteurs seront beaucoup plus long à calculer sur une machine moyenne.
- DINOSv2: modèle plus lourd que CLIP, censé avoir de meilleures performances sur la similarité visuelle, ne permet pas de faire de la similarité texte / image

## Créer de nouveaux vecteurs

Afin de pouvoir tester ces différents modèles, il faut générer les vecteurs associés à ce modèle, on se rend donc dans les paramètres du projet:

![Alt text](../images/params_projets01.png)

- Puis on se rend dans Vecteurs > Créer de nouveaux vecteurs.
- On choisit le nom du modèle que l'on souhaite utiliser, dans l'exemple ci-dessous SIGLIP
- On confirme en appuyant sur Créer et le calcul devrait se lancer en quelques secondes

![Alt text](../images/create_vectors.png)

!!! note

    Il est possible d'également cocher l'option "greyscale" avant d'appuyer sur "Créer" si l'on souhaite ignorer la couleur des images, cela peut être utile par exemple dans un corpus possédant des images en noir et blanc et d'autres en couleurs si jamais on ne souhaitait pas que la couleur soit un critère déterminant par rapport à ce qui est représenté à l'image.

!!! note

    Dans le cas où pour une raison quelconque le calcul des vecteurs venait à être interrompu il est possible de le relancer en appuyant sur le bouton suivant:
    ![Alt text](../images/restart_vector_compute.png)


## Utiliser les vecteurs

Une fois généré, les nouveaux vecteurs ne sont pas utilisés par défaut, comme les autres vecteurs (CLIP par exemple) restent disponibles il faut choisir lorsque l'on execute une action quels vecteurs l'on souhaite utiliser.

Ainsi dans n'importe quelle action de similarité panoptic, clustering, similarité visuelle, similarité textuelle, recommandation de groupe, il est toujours possible de préciser quels vecteurs utiliser: 

- Lors de l'execution d'une fonction on appuie sur vec_type et on vient choisir les vecteurs que l'on vient de générer:

![Alt text](../images/select_vector.png)

