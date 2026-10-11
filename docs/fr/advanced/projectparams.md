# Paramètres de projet et de plugins

Il est possible de gérer un certain nombre d'options dans les paramètres de projets.

Pour y accéder il faut cliquer sur la petite roue dentée à côté du nom du projet ouvert dans l'interface. Les paramètres sont organisés en quatre sections : Images, Vecteurs, Extensions et Données.

## Images

![Alt text](../images/v1/parametres-images.png)

Cette section indique les tailles d'images enregistrées dans le projet lors de l'import : par défaut "small" (256 px) et "large" (1024 px). La colonne "Stored" indique pour combien d'images chaque taille a été calculée. "Ajouter un type d'image" permet d'enregistrer une taille supplémentaire, voire l'image complète, ce qui rend le dossier du projet plus autonome et plus facilement partageable à d'autres personnes sans que ces dernières n'aient besoin des images. Le bouton "Recalculer toutes les miniatures manquantes" relance le calcul si certaines images n'ont pas été traitées.

## Vecteurs

Cette section liste les vecteurs disponibles pour le projet et permet d'en créer de nouveaux à partir d'autres modèles (voir [Choisir son modèle](/advanced/models/)).

## Extensions

![Alt text](../images/v1/parametres-extensions.png)

Pour chaque plugin installé, cette section affiche sa description, son état ("Actif" ou "Arrêté") et ses paramètres. Pour le plugin de similarité, on peut par exemple choisir de calculer automatiquement les vecteurs à l'import des images (compute_on_import) ou d'enregistrer les recherches textuelles (save_text_searches). "Arrêter le plugin" le met en pause pour ce projet jusqu'à sa réouverture.

## Données

![Alt text](../images/v1/parametres-donnees.png)

Chaque modification apportée au projet (annotation, import, création de propriété...) est enregistrée sous la forme d'un "commit", avec sa date et son auteur. Cette section liste tous les commits du projet. L'interrupteur de la colonne "Actif" permet de désactiver un commit, ce qui annule ses modifications sans les supprimer, et de le réactiver plus tard.

!!! Attention
    "Compacter jusqu'ici" fusionne définitivement tout l'historique jusqu'au commit choisi. Les commits antérieurs ne pourront alors plus être désactivés individuellement.

## Activer ou désactiver les plugins pour un projet

Lorsque l'on installe un plugin dans panoptic, il est automatiquement activé pour tous les projets. Mais en réalité tous les projets n'auront pas forcément besoin de tous les plugins, ainsi un projet sans image contenant du texte n'aura pas besoin du plugin d'OCR. 
Il est donc ainsi possible de désactiver les plugins non nécessaires à un projet, depuis la page d'accueil en cliquant sur les trois petits points à côté du nom du projet:

![Alt text](../images/v1/accueil-projet-options.png)

Il suffira ensuite de cocher ou décocher les plugin à activer / désactiver.
