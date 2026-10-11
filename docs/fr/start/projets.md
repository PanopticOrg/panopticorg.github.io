# Les Projets

Panoptic permet de travailler avec vos corpus, localement, sur votre ordinateur. Panoptic ne propose donc pas de collections d'images prédéfinies, les jeux de données doivent être constitués en amont.

Toutes les actions réalisées au sein d'un projet sont automatiquement sauvegardées, localement, sur votre ordinateur. Si vous fermez un projet, avant d'y revenir plus tard, vous y retrouverez toutes les actions que vous y avez effectuées.

Panoptic permet de travailler avec autant de projets qu'on le souhaite.

Dans un projet, vous pouvez travailler avec plusieurs corpus d'images si vous le souhaitez, importés en une seule fois ou en plusieurs fois.

## Page de gestion des projets Panoptic

![image](../images/v1/accueil.png)

Les projets se gèrent dans une page dédiée (création, importation, suppression), qui est la page d'accueil de Panoptic : elle s'ouvre lors du lancement du logiciel et reste accessible n'importe quand.
            
Dans la page de gestion de projets, cliquez sur "Créer" à côté de "Créer un nouveau projet".

![image](../images/v1/creer-projet.png)

Il s'agit alors de définir l'endroit dans votre ordinateur (le "dossier") où vous voulez enregistrer votre projet. Cliquez sur l'icône de dossier à droite du champ "Dossier" : un explorateur de fichiers s'ouvre. Naviguez jusqu'au dossier souhaité puis cliquez sur "Sélectionner".

![image](../images/v1/creer-projet-dossier.png)

!!! Attention
    Il ne faudra pas bouger ce dossier/en renommer le chemin ensuite.
    
    Créez ce dossier dans un dossier différent de celui qui contient votre corpus d'images.
    
    Créez donc au préalable, où cela vous arrange, un dossier "panoptic" dans lequel vous viendrez enregistrer tous vos projets à l'avenir.

Nommez ensuite votre projet dans le champ "Nom du projet". Panoptic créera un sous-dossier portant ce nom dans le dossier choisi.

Faites enfin "Créer" : votre projet est créé et la page de travail de Panoptic s'ouvre.

![image](../images/v1/projet-vide.png)
     
## Accéder à un projet existant

Lorsque vous ouvrez Panoptic, choisissez à gauche le projet que vous souhaitez ouvrir en cliquant dessus. 

Les trois petits points à droite du nom d'un projet permettent de le supprimer de la liste ("delete") ou de choisir les plugins actifs pour ce projet (voir [Paramétrer un projet](/advanced/projectparams/)).

![image](../images/v1/accueil-projet-options.png)
    
Si vous êtes déjà dans un projet ouvert et que souhaitez changer de projet, en haut à gauche, cliquez sur la flèche.

## Projets créés avec une ancienne version

Les projets créés avec une version de Panoptic antérieure à la v1 doivent être convertis avant de pouvoir être ouverts. S'il en trouve, Panoptic l'indique sur la page d'accueil par un bandeau "Des projets d'une ancienne version ont été trouvés" et par la mention "Créé avec une ancienne version de Panoptic" sous le nom des projets concernés. Cliquez sur "Convertir" pour lancer la conversion.

!!! Important
    La conversion crée une copie du projet original, qui reste intact. Les onglets ne sont pas conservés et les vecteurs doivent être recalculés par le plugin de similarité.

## Utilisateurs

En bas de la page d'accueil, la section "Utilisateur" permet de choisir sous quel nom vous travaillez. Par défaut, toutes les modifications sont enregistrées au nom de l'utilisateur "Par défaut". Pour créer un nouvel utilisateur, cliquez sur "Par défaut" puis sur "Nouvel utilisateur", entrez un nom et validez.

![image](../images/v1/utilisateurs.png)

Cela est utile lorsque plusieurs personnes annotent un même projet à tour de rôle : l'historique des modifications (voir [Astuces et raccourcis](/advanced/astuces/)) permet ensuite de distinguer ses propres modifications de celles des autres.
