# Les onglets 

Comme abordé brièvement précédemment, panoptic propose un système d'onglets permettant de conserver différents points de vue en parallèle sur le même corpus. 

Les onglets se trouvent en haut à droite de l'écran. Le "+" crée un nouvel onglet, un double clic sur le nom d'un onglet permet de le renommer, et la flèche ouvre la liste de tous les onglets du projet.

![Alt text](../images/v1/onglets.webp)

Chaque onglet a ses propres [filtres, tris et groupes](/start/filters/), ainsi que sa propre [vue](/start/vues/) et ses propriétés affichées. Passer d'un onglet à l'autre permet donc de retrouver instantanément chaque espace de travail dans l'état où on l'a laissé.

Les onglets sont également propres à chaque [utilisateur](/start/projets/#utilisateurs) : lorsque plusieurs personnes travaillent sur un même projet, chacune retrouve ses propres onglets, sans modifier ceux des autres. Les annotations, elles, restent communes à tout le projet.

## Exemple de cas d'usage

L'objectif est de pouvoir créer des espace de travail dédiés à certains objets à l'aide des filtres des tris et des groupes. Un exemple basique est l'utilisation d'un onglet "poubelle". On utilise un premier onglet d'exploration, dans lequel on annote les images avec une propriété de type checkbox "hors corpus" tout en appliquant un filtre sur cette propriété. Toutes les images qui sont cochées disparaissent alors instantanément du premier onglet grâce à ce filtre et aparaissent dans un autre onglet qui a le filtre inverse (c'est à dire ne laissant apparaître que les images qui ont la case "hors corpus" de cochée). Cela permet de revenir de temps en temps se concentrer sur l'onglet "poubelle" afin de revisionner les images qui ont été désignées comme hors corpus et de vérifier que l'on a pas fait d'erreur, sans pour autant devoir voir ces images là dans la vue principale.
