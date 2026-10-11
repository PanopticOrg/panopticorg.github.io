# Installer un plugin

Installer un plugin est (normalement) relativement facile, il suffit d'avoir l'adresse d'un répertoire github (ou gitlab) sur lequel le code du plugin est stocké.
Par exemple: https://github.com/PanopticOrg/PanopticOCR

Dans panoptic il faut ensuite se rendre sur la page d'accueil et cliquer sur le + à côté de "Plugins". Trois icônes permettent de choisir la source du plugin : un répertoire git (par défaut), un paquet python publié sur PyPI, ou un dossier présent sur votre ordinateur.

On rentre ensuite l'url git, on clique dans le champ nom (qui devrait se remplir automatiquement à partir de l'url) puis on clique sur Installer.

![Alt text](../images/v1/plugins-ajout.png)

Le plugin devrait alors s'installer et une fois fini il devient disponible pour tous les projets. Il est ensuite possible de le désactiver pour certains projets (voir [Paramétrer un projet](/advanced/projectparams/)).

Les trois petits points à droite du nom d'un plugin, sur la page d'accueil, permettent de le mettre à jour, de le réinstaller ou de le supprimer.
