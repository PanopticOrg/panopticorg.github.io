# Installation Serveur

Panoptic est avant tout pensé pour être utilisé localement, mais il est également possible de l'installer sur un serveur (par exemple une machine de calcul de votre laboratoire, dotée d'une carte graphique et de beaucoup de mémoire) puis de l'utiliser depuis le navigateur d'un autre ordinateur. Les images, les projets et les calculs restent alors sur le serveur, et il suffit d'un navigateur pour travailler.

!!! warning "Sécurité"

    Panoptic ne possède pas de système d'authentification : toute personne capable de joindre le serveur sur le port de Panoptic peut consulter et modifier les projets. Le mode serveur est donc à réserver à un réseau de confiance (réseau interne, VPN), ou à placer derrière un reverse proxy qui gère l'authentification. Le paramètre `data_paths` décrit plus bas permet en outre de limiter les dossiers du serveur accessibles depuis Panoptic.

## Installation

L'installation est la même que l'installation standard avec python (voir [Installation Standard](/install/install/#avec-python)), de préférence dans un environnement virtuel :

```sh
python3 -m venv panoptic_env
source panoptic_env/bin/activate
pip3 install panoptic
```

Le serveur n'ayant généralement pas d'écran, le plugin de similarité peut être installé directement en ligne de commande :

```sh
panoptic plugins add vision
```

La commande `panoptic plugins list` permet ensuite de vérifier les plugins installés. Les plugins peuvent aussi être ajoutés plus tard depuis la page d'accueil, comme sur une installation classique.

## Lancement

Pour lancer Panoptic en mode serveur, il faut lui indiquer d'accepter les connexions venant d'autres machines (paramètre `host`, voir plus bas) et de ne pas chercher à ouvrir de navigateur sur le serveur (variable d'environnement `PANOPTIC_REMOTE`) :

```sh
PANOPTIC_REMOTE=1 PANOPTIC_HOST=0.0.0.0 panoptic
```

Panoptic est alors accessible depuis n'importe quel ordinateur du réseau à l'adresse `http://adresse-du-serveur:8000`.

En pratique, il est plus simple de regrouper tous les réglages dans un fichier de configuration :

```sh
PANOPTIC_REMOTE=1 panoptic --config /chemin/vers/panoptic.toml
```

!!! note

    `PANOPTIC_REMOTE` ne se règle que par variable d'environnement. En plus d'empêcher l'ouverture du navigateur, elle active par défaut la compression des réponses (paramètre `gzip`), ce qui accélère l'ouverture des projets à travers le réseau.

## Le fichier de configuration

Le fichier de configuration est un fichier texte au format [TOML](https://toml.io/fr/). Panoptic le cherche dans cet ordre :

1. le fichier indiqué avec l'option `--config` : `panoptic --config panoptic.toml`,
2. le fichier indiqué par la variable d'environnement `PANOPTIC_CONFIG`,
3. le fichier `~/.panoptic/panoptic_config.toml`, s'il existe.

Sans fichier de configuration, Panoptic utilise ses valeurs par défaut. Le fichier de configuration n'est donc pas réservé au mode serveur : sur un ordinateur personnel, créer `~/.panoptic/panoptic_config.toml` permet par exemple de changer le port ou la base utilisée sans avoir à le préciser à chaque lancement.

Voici un exemple de fichier complet :

```toml
# Base principale de Panoptic (liste des projets et des plugins)
db = "/srv/panoptic/base"

# Port et adresse d'écoute
port = 8000
host = "0.0.0.0"

# Compression des réponses
gzip = true

# Rechargement automatique des plugins (développement)
watch_plugins = false

# Dossiers accessibles depuis Panoptic
data_paths = [
    { path = "/srv/panoptic/images", alias = "Images" },
    { path = "/mnt/archives" },
]
```

Tous les paramètres sont facultatifs : seuls ceux que l'on souhaite modifier ont besoin d'apparaître dans le fichier. Un paramètre inconnu ou mal écrit empêche Panoptic de se lancer et un message indique l'erreur, ce qui évite qu'une faute de frappe passe inaperçue.

!!! note "Chemins relatifs"

    Les chemins relatifs (`db`, `data_paths`) sont interprétés à partir du dossier qui contient le fichier de configuration, et non à partir du dossier depuis lequel on lance Panoptic. Le caractère `~` peut être utilisé pour désigner le dossier personnel.

### Priorité des réglages

Chaque réglage peut être défini à plusieurs endroits. En cas de conflit, c'est l'option de la ligne de commande qui l'emporte, puis la variable d'environnement, puis le fichier de configuration, et enfin la valeur par défaut. On peut ainsi garder un fichier de configuration commun et changer ponctuellement le port avec `PANOPTIC_PORT=8001 panoptic`.

## Les paramètres

| Paramètre | Valeur par défaut | Variable d'environnement | Option | Rôle |
| --- | --- | --- | --- | --- |
| `db` | `~/.panoptic/panoptic.db` | `PANOPTIC_DB` | `--db` | Base principale de Panoptic |
| `port` | `8000` | `PANOPTIC_PORT` | | Port sur lequel Panoptic est accessible |
| `host` | aucune (connexions locales uniquement) | `PANOPTIC_HOST` | | Adresse d'écoute du serveur |
| `gzip` | activé si `PANOPTIC_REMOTE` est défini | | | Compression des réponses volumineuses |
| `watch_plugins` | `false` | `PANOPTIC_WATCH_PLUGINS=1` | | Rechargement automatique des plugins |
| `data_paths` | aucun (tous les dossiers) | | | Dossiers accessibles depuis Panoptic |

### db

Chemin de la base principale de Panoptic, qui contient la liste des projets, des plugins et des utilisateurs. Il peut s'agir d'un fichier `.db` ou d'un dossier, auquel cas la base sera le fichier `panoptic.db` de ce dossier. Les plugins sont installés à côté de la base, dans un dossier `plugins`.

Utiliser une autre base permet par exemple de séparer complètement deux usages de Panoptic sur une même machine, chacun avec sa propre liste de projets et ses propres plugins. Les données des projets, elles, restent toujours dans le dossier de chaque projet (voir [Partager un projet](/advanced/projectimport/)).

### port

Port sur lequel Panoptic est accessible, `8000` par défaut. Il faut le changer si ce port est déjà utilisé sur la machine, ou pour faire tourner deux instances de Panoptic en même temps (chacune avec sa propre base).

### host

Adresse sur laquelle Panoptic attend les connexions. Par défaut, seul l'ordinateur sur lequel tourne Panoptic peut s'y connecter. Avec `host = "0.0.0.0"`, Panoptic accepte les connexions de toutes les machines qui peuvent joindre le serveur : c'est le réglage nécessaire au mode serveur (voir l'avertissement de sécurité en haut de cette page).

### gzip

Compresse les réponses volumineuses du serveur, en particulier les propriétés d'un projet envoyées à son ouverture. La compression demande un peu de calcul au serveur mais réduit fortement la quantité de données à transférer, ce qui est intéressant à travers un réseau et inutile en local. Elle est activée par défaut lorsque `PANOPTIC_REMOTE` est défini, et désactivée sinon. Elle peut être forcée dans un sens ou dans l'autre avec `gzip = true` ou `gzip = false`.

### watch_plugins

Recharge automatiquement un plugin lorsque l'un de ses fichiers est modifié, sans avoir à relancer Panoptic. Ce paramètre est surtout utile pour le développement de plugins (voir [Créer ses plugins](/plugins/dev/)) et peut rester désactivé dans les autres cas.

### data_paths

Liste des dossiers accessibles depuis Panoptic. Chaque dossier est décrit par son chemin (`path`) et, éventuellement, par le nom sous lequel il apparaît dans l'interface (`alias`, par défaut le nom du dossier).

Sans ce paramètre, l'explorateur de fichiers de Panoptic permet de parcourir tout le disque de la machine, ce qui est pratique en local mais rarement souhaitable sur un serveur. Lorsqu'il est défini, seuls ces dossiers (et leurs sous-dossiers) peuvent être parcourus, utilisés pour créer ou importer un projet, ajoutés comme source d'images ou servis au navigateur. Toute tentative d'accéder à un autre dossier est refusée.

Dans l'explorateur de fichiers, les dossiers autorisés apparaissent alors dans la section "Accès rapide", sous leur alias, et la liste des disques est vide :

![Alt text](../images/v1/serveur-dossiers.png)

!!! note

    Les projets sont eux aussi créés dans un dossier : il faut donc que `data_paths` contienne au moins un dossier où Panoptic peut écrire, en plus des dossiers d'images.

## Avec Docker

L'image Docker de Panoptic (voir [Installation avec Docker](/install/install/#installation-avec-docker)) est déjà configurée pour le mode serveur : elle accepte les connexions extérieures et n'essaie pas d'ouvrir de navigateur. Il suffit de rendre le port accessible avec l'option `-p 8000:8000` de Docker.
