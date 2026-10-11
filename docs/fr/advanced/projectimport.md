# Partager un projet

Il est possible d'importer un projet déjà existant, ce qui permet de transférer un projet d'un ordinateur à l'autre. 
Il suffit pour cela de copier le dossier du projet sur l'autre ordinateur, puis de cliquer sur "Importer" depuis la page d'accueil, et de naviguer jusqu'au dossier du projet que l'on souhaite importer. Les dossiers reconnus comme des projets Panoptic sont signalés par l'icône de Panoptic. Cliquez enfin sur "Sélectionner".

![Alt text](../images/v1/import-projet.png)

!!! info
    Un avantage d'importer un projet c'est que cela permet de ne pas recalculer les vecteurs d'images, ces derniers sont déjà automatiquement stockés dans le dossier du projet.
    Un usage courant est donc de calculer les vecteurs sur un ordi puissant puis de partager le projet pour de l'exploration sur des ordinateurs moins puissants.

## Contenu du dossier d'un projet

Le dossier d'un projet contient notamment :

- data.db : les propriétés, les tags et toutes les annotations,
- media.db : les miniatures des images et les vecteurs,
- project.db : les onglets et les paramètres du projet,
- exports : les exports réalisés depuis ce projet.

C'est donc l'ensemble du dossier qu'il faut copier pour partager ou sauvegarder un projet.

## Intégrer les images

Il convient tout de même de noter que les images originales ne sont pas copiées dans le projet : seules des versions réduites y sont enregistrées. Par défaut, Panoptic conserve deux tailles, "small" (256 px) et "large" (1024 px), ce qui suffit pour explorer et annoter le projet sur un autre ordinateur sans avoir besoin des images d'origine. Ces tailles peuvent être modifiées dans les [paramètres du projet](/advanced/projectparams/).
