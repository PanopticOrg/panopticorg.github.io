# Installation (Fin)

!!! info

    Si vous avez installé panoptic avec un script / un exe ou en utilisant panoptic[vision] cette étape peut être ignorée

    
Par soucis de flexibilité, Panoptic est installé sans les outils de similarité. Dans la plupart des cas vous voudrez les installer pour utiliser les fonctionnalités de clustering et de similarité d'image.

Au premier lancement, si le plugin n'est pas encore installé, une fenêtre d'accueil vous propose de le faire : il suffit de cliquer sur "Installer le plugin de similarité". Ce même bouton reste disponible sur la page d'accueil de panoptic, dans la section "Plugins". Cela prendra quelques instants car les librairies peuvent être un peu lourdes à télécharger (plusieurs centaines de Mo).

![image](../images/v1/premier-lancement.png)

Une fois l'installation terminée, le bouton affiche "Installé" et le plugin "PanopticML" apparaît dans la liste des plugins de la page d'accueil.

!!! warning "Utilisation d'une carte graphique"

    Si vous possédez une carte graphique (GPU), cela peut accélérer le fonctionnement de panoptic lors de l'import des images. Toutefois, en fonction de la manière dont vous avez installé panoptic et de votre système d'exploitation vous n'aurez pas toujours les librairies GPU d'installées par défaut. Des informations d'installation des versions cuda de pytorch sont disponibles pour chaque OS sur [ce lien](https://pytorch.org/get-started/locally/).

    A noter que l'execution de panoptic ne sera pas impactée si vous ne possédez pas de GPU, seul l'import des images (qui ne se produit qu'une fois) sera plus lent.
