# Installation

!!! warning "Prérequis matériels"

    Panoptic a été pensé et conçu pour être éxecuté sur un ordinateur local. De nombreux efforts d'optimisations ont été effectués pour que le logiciel puisse tourner sur le plus de machines possibles, néanmoins plus le nombre d'images augmentera et plus une machine dotée d'un bon processeur et d'au moins 16Go de RAM sera conseillée pour une bonne expérience d'utilisation.


## Avec python

### Installation

Si vous avez déjà python d'installé, avec une version supérieure ou égale à `3.10` vous pouvez simplement éxecuter dans un terminal: 

=== "Windows (cmd)"

    ```bash
    pip install panoptic
    ```

=== "macOS / Linux"

    ```sh
    pip3 install panoptic
    ```

!!! warning "Utilisateurs Mac OS"

    Les outils xcode ont besoin d'être installés préalablement pour que panoptic puisse fonctionner convenablement sur MacOS. 

    Ces derniers peuvent être installés via:
    `xcode-select --install`


#### Lancement 

Entrez la commande `panoptic` dans votre terminal

### Utilisation d'un environnement virtuel (recommandé)

Les paquets python pouvant facilement entrer en conflits en fonction des versions il est conseillé d'installer panoptic dans un environnement python dédié. 

=== "Windows (cmd)"

    ```bash
    python -m venv panoptic_env
    panoptic_env\Scripts\activate
    pip install panoptic
    ```

=== "macOS / Linux"

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

=== "macOS / Linux"

    ```sh
    source panoptic_env/bin/activate
    panoptic
    ```

## Avec des scripts

### Installation 

Si vous n'avez pas encore python, ou ne souhaitez pas créer l'environnement vous même, vous pouvez utiliser nos scripts d'installation de la manière suivante:

=== "Windows (cmd)"

    Un executable est disponible [sur ce lien](https://github.com/CERES-Sorbonne/Panoptic/blob/main/install/windows/panoptic.exe) et permet d'installer et de lancer Panoptic au sein d'un environnement virtuel. 

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
