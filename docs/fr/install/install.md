# Installation

!!! warning "Prérequis matériels"

    Panoptic a été pensé et conçu pour être éxecuté sur un ordinateur local. De nombreux efforts d'optimisations ont été effectués pour que le logiciel puisse tourner sur le plus de machines possibles, néanmoins plus le nombre d'images augmentera et plus une machine dotée d'un bon processeur et d'au moins 16Go de RAM sera conseillée pour une bonne expérience d'utilisation.


## Avec l'application de bureau (recommandé)

Panoptic est disponible sous la forme d'une application de bureau, qui s'occupe à la fois de l'installation, des mises à jour et du lancement. Panoptic s'ouvre alors dans sa propre fenêtre et non plus dans un navigateur web, ce qui lui permet d'offrir de meilleures performances.

### Installation

Les installateurs se trouvent [sur cette page](https://github.com/CERES-Sorbonne/Panoptic/releases/tag/desktop-latest), dans la section "Assets" :

=== "Windows"

    Téléchargez le fichier `Panoptic_x.x.x_x64-setup.exe` puis lancez-le.

=== "Linux"

    Téléchargez le fichier `.deb` (Ubuntu, Debian...) ou `.rpm` (Fedora...) correspondant à votre distribution, puis installez-le, par exemple :

    ```sh
    sudo apt install ./Panoptic_x.x.x_amd64.deb
    ```

=== "macOS"

    Téléchargez le fichier `Panoptic_x.x.x_universal.dmg`, ouvrez-le puis glissez Panoptic dans le dossier Applications. Il fonctionne aussi bien sur les Mac récents (Apple Silicon) que sur les plus anciens (Intel).

!!! warning "Application non signée"

    L'application n'est pas encore signée, votre système peut donc refuser de l'ouvrir la première fois. Sur macOS, autorisez son ouverture dans les réglages "Confidentialité et sécurité". Sur Windows, cliquez sur "Informations complémentaires" puis sur "Exécuter quand même".

### Premier lancement

Au premier lancement, l'application installe elle-même tout ce dont Panoptic a besoin. Une connexion internet est nécessaire pour cette étape, qui peut prendre plusieurs minutes :

1. l'application demande d'abord dans quel dossier installer Panoptic (par défaut, le dossier `panoptic` de votre dossier personnel). C'est dans ce dossier que seront placés l'environnement python de Panoptic et les logs, vos projets pourront être créés n'importe où ailleurs,
2. sur Windows et Linux, elle demande ensuite si vous possédez une carte graphique NVidia, afin d'installer la version adaptée : la version pour carte graphique accélère l'importation des images, mais prend plus de place sur le disque,
3. elle installe enfin Panoptic et le plugin de similarité, en affichant le détail de l'installation, puis ouvre la page d'accueil de Panoptic.

Aux lancements suivants, Panoptic s'ouvre directement. Lorsqu'une nouvelle version est disponible, l'application propose de l'installer avant de démarrer. Il est possible de refuser et de garder la version actuelle.

!!! note

    En cas d'erreur pendant l'installation, le message d'erreur et un bouton "Réessayer" s'affichent dans la fenêtre. Le chemin du fichier de logs, utile pour signaler un problème, est indiqué en bas de la fenêtre.

### Changer de base Panoptic

Sur la page d'accueil, sous le numéro de version, l'application affiche la base Panoptic utilisée, c'est à dire le fichier qui contient la liste de vos projets et de vos plugins. Les liens situés en dessous permettent d'ouvrir une autre base existante, d'en créer une nouvelle ou de revenir à la base par défaut. Panoptic redémarre alors sur la base choisie.

## Avec des fichiers d'installation

### Installation 

Cette installation à base de script permet d'installer la bonne version de python, ainsi que toutes les dépendances pour être sûr d'être compatible:

!!! note

    Il vous sera demandé au milieu de l'installation si vous souhaitez installer une version pour carte graphique. Cela permet d'accéler l'importation des images qui peut être longue mais prendra plus de place sur votre disque.
    Il est important de noter que cela ne fonctionne qu'avec des cartes graphiques NVidia.





=== "Windows"

    Un executable est disponible [sur ce lien](https://github.com/CERES-Sorbonne/Panoptic/raw/refs/heads/main/install/windows/panoptic.exe) et permet d'installer et de lancer Panoptic au sein d'un environnement virtuel. 

=== "Linux"

    ```sh
    wget https://raw.githubusercontent.com/CERES-Sorbonne/Panoptic/refs/heads/main/install/start_panoptic_linux.sh -O start_panoptic_linux.sh
    chmod +x start_panoptic_linux.sh
    ./start_panoptic_linux.sh
    ```

=== "macOS"

    ```sh
    curl -O https://raw.githubusercontent.com/CERES-Sorbonne/Panoptic/refs/heads/main/install/start_panoptic_mac.sh
    chmod +x start_panoptic_mac.sh
    ./start_panoptic_mac.sh
    ```

### Lancement

=== "Windows (cmd)"

    Il suffit de lancer panoptic.exe 

=== "Linux"

    ```sh
    ./start_panoptic_linux.sh
    ```

    D'autre part le script ajoute normalement également une icone permettant de lancer panoptic depuis un clic sur l'icone.


=== "macOS"

    ```sh
    ./start_panoptic_mac.sh
    ```

## Avec python

### Installation

Si vous avez déjà python d'installé, avec une version supérieure ou égale à `3.10` vous pouvez simplement éxecuter dans un terminal: 

=== "Windows (cmd)"

    ```bash
    pip install panoptic
    ```

=== "Linux"

    ```sh
    pip3 install panoptic
    ```

=== "macOS"

    ```sh
    pip3 install panoptic
    ```

!!! warning "Utilisateurs Mac OS"

    Les outils xcode ont besoin d'être installés préalablement pour que panoptic puisse fonctionner convenablement sur MacOS. 

    Ces derniers peuvent être installés via:
    `xcode-select --install`

    D'autre part, de nombreuses dépendances doivent avoir des versions précises pour fonctionner sous mac. Il est ainsi recommandé d'utiliser le script d'installation de panoptic fourni plus bas.

!!! note

    Dans les trois cas il est possible de remplacer `panoptic` dans la commande par `panoptic[vision]` pour installer panoptic avec le module de similarité directement

    
#### Lancement 

Entrez la commande `panoptic` dans votre terminal

!!! note

    Par défaut, Panoptic enregistre la liste de vos projets et de vos plugins dans `~/.panoptic/panoptic.db`. Il est possible d'utiliser une autre base avec `panoptic --db chemin/vers/dossier`.

### Utilisation d'un environnement virtuel

Les paquets python pouvant facilement entrer en conflits en fonction des versions il est conseillé d'installer panoptic dans un environnement python dédié. 

=== "Windows (cmd)"

    ```bash
    python -m venv panoptic_env
    panoptic_env\Scripts\activate
    pip install panoptic
    ```

=== "Linux"

    ```sh
    python3 -m venv panoptic_env
    source panoptic_env/bin/activate
    pip3 install panoptic
    ```

=== "macOS"

    ```sh
    python3 -m venv panoptic_env
    source panoptic_env/bin/activate
    pip3 install panoptic
    ```

#### Lancement

=== "Windows (cmd)"

    ```bash
    panoptic_env\Scripts\activate
    panoptic
    ```

=== "Linux"

    ```sh
    source panoptic_env/bin/activate
    panoptic
    ```

=== "macOS"

    ```sh
    source panoptic_env/bin/activate
    panoptic
    ```



## Installation avec Docker

Si vous avez rencontré des problèmes avec l'installation classique, ou que vous préférez utiliser Docker, une image est à disposition. Il faut tout d'abord:

### Installer Docker
- [Sur MacOS](https://docs.docker.com/desktop/install/mac-install/)
- [Sur Windows](https://docs.docker.com/desktop/install/windows-install/)
- [Sur Linux](https://docs.docker.com/desktop/install/linux-install/)


### Option 1: Un seul dossier pour les images et pour les données panoptic:

Cela implique d'avoir créé un dossier spécial appelé "images", dans le dossier que vous indiquerez en entrée de panoptic. Dans l'exemple suivant, il faudrait ainsi que dans le dossier: `/chemin/vers/le/dossier`, il existe un dossier `images` dont le chemin complet serait par conséquent `/chemin/vers/le/dossier/images`.

Il faut ensuite lancer la commande suivante (avec Docker de lancé au préalable)

```bash
docker run -it -p 8000:8000 -v /path/to/your/folder:/data --name panoptic ceressorbonne/panoptic
```

### Option 2: Un dossier pour les images, et un dossier pour les données panoptic:

```bash
docker run -it -p 8000:8000 \
-v /path/to/your/data:/data \
-v /path/to/your/images:/data/images \
--name panoptic \
ceressorbonne/panoptic
```
