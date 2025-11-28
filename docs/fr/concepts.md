# Glossaire

Cette page est un aperçu de tous les concepts utilisés dans Panoptic. Elle peut être une bonne référence pour comprendre rapidement un terme ou obtenir une vue d'ensemble du logiciel. Pour plus d’informations sur un concept spécifique, consultez la page dédiée.

## Projet

Les projets dans Panoptic sont un moyen de stocker votre travail. Vous pouvez, par exemple, créer différents projets sur un même corpus si vous souhaitez réaliser différentes annotations, importer différentes données en lien avec les images, ou encore mélanger plusieurs corpus d'images dans un même projet.

Par exemple, il peut être intéressant de travailler sur un ensemble de photographies historiques pour faire des annotations et explorer les thèmes récurrents, mais il pourrait également être pertinent de mélanger ce corpus avec un corpus collecté sur Internet afin de voir si certaines de ces images historiques peuvent être retrouvées sur des sites web et, si oui, dans quel contexte elles apparaissent.

### Données

Lors de la création d'un projet, vous devez sélectionner un dossier dans lequel les données du projet seront stockées.
Chaque projet stocke ses données séparément dans une base de données SQLite [(voir le schéma détaillé)](https://github.com/CERES-Sorbonne/Panoptic/wiki/SQL-Schema).

### Paramètres

Un projet peut être configuré avec des paramètres permettant de définir les valeurs par défaut de chaque plugin au niveau du projet. Il est également possible, par exemple, de stocker une copie des images directement dans la base de données, ce qui facilite le partage d’un projet Panoptic en envoyant un seul fichier.

## Images et Instances

L’un des concepts les plus complexes à comprendre dans Panoptic est la différence entre images et instances.
Pour comprendre la nécessité de cette distinction, prenons l’exemple d’une image trouvée sur Twitter, mais postée par deux utilisateurs différents, à des moments différents, et avec des messages très distincts. Techniquement, c’est la même image, mais comme les contextes dans lesquels elle apparaît sont très différents, on pourrait considérer qu'elle n'est pas sémantiquement identique.

Ainsi, si nous souhaitons observer les images dans Panoptic avec leurs contextes stockés sous forme de propriétés, une même image peut apparaître plusieurs fois si elle a été trouvée plusieurs fois dans le corpus avec des propriétés différentes.

En résumé :

- Une **image** correspond uniquement à un ensemble de pixels.
- Une **instance d'image** représente l'occurrence de cet ensemble de pixels dans un contexte spécifique.

Par conséquent, une image peut avoir plusieurs instances, mais une instance ne peut être liée qu'à une seule image.

## Propriétés

Les propriétés sont utilisées dans Panoptic pour ajouter des données supplémentaires qui ne sont pas des images. Elles peuvent être importées ou ajoutées manuellement afin de créer des annotations sur les images.

### Types de propriétés

Les propriétés peuvent être de différents types selon le type d'annotation à ajouter. Chaque type possède un comportement spécifique. Par exemple, les propriétés de type date permettent de regrouper dynamiquement les images par année, mois, semaine, etc.

| Type de propriété | Description |
| --- | --- |
| Tag | Contient un seul tag |
| MultiTags | Contient plusieurs tags |
| URL | Lien web cliquable |
| Date | Une date |
| Couleur | Une couleur parmi 12 disponibles dans Panoptic |
| Checkbox | Case à cocher simple |
| Nombre | Nombre entier ou flottant |
| Texte | Donnée textuelle |

### Image / Instance

Lorsqu'elles sont créées ou importées, les propriétés peuvent être liées aux images ou aux instances :

- Une **propriété d'image** est partagée par toutes les instances de cette image et est souvent utilisée pour décrire des caractéristiques visuelles.
- Une **propriété d'instance** est liée à une seule occurrence spécifique d'une image.

Par exemple, pour une même image postée deux fois sur Twitter, les auteurs, la date de publication et le commentaire associé au post doivent être des propriétés d'instance et non des propriétés d’image.

### Tags

Les types de propriété les plus couramment utilisés dans Panoptic sont "tag" et "multi_tags" car ils sont faciles à créer et à manipuler, avec une autocomplétion facilitant l'annotation des images. Cependant, lorsqu’il y a un grand nombre de tags, leur organisation peut devenir complexe. Dans Panoptic, les tags peuvent être **hiérarchiques** et avoir **plusieurs parents**.

C'est pourquoi un module dédié à la gestion des tags a été créé, souvent appelé "tags modal", permettant de réorganiser ou renommer les tags visuellement.

### Importation

Les propriétés peuvent être importées via le module d'importation en utilisant un fichier CSV.

### Exportation

Les propriétés peuvent être exportées via le module d'exportation vers un fichier CSV. Une sélection d'images peut également être exportée avec le fichier CSV.

## Filtres, Tri et Groupes

Panoptic permet de créer des vues dynamiques des images en utilisant des filtres, des tris et des regroupements.

### Filtres

Les filtres permettent d'afficher uniquement les images correspondant aux critères définis. Plusieurs filtres peuvent être combinés à l'aide des opérateurs **ET** ou **OU**.

### Tri

Le tri permet de modifier l’ordre d’affichage des images. Il peut être **croissant** ou **décroissant** et appliqué sur plusieurs propriétés, par exemple :
"trier par date croissante, puis par description textuelle décroissante".

### Groupes

Les groupes permettent de regrouper les images en fonction d'une propriété sélectionnée. Des sous-groupes peuvent être créés en sélectionnant une autre propriété. Les groupes peuvent être triés par valeur de propriété ou par nombre d'éléments.

### Recherche

Une recherche en texte intégral est possible sur toutes les propriétés textuelles via la barre de recherche.

## Vues

Lors de l'affichage des images, plusieurs modes de présentation sont disponibles :

- **Vue en grille** : affichage par défaut centré sur les images.
- **Vue en tableau** : permet de visualiser plus de propriétés et/ou des propriétés longues.
- **Vue en graphe** : affiche un graphe lorsqu'un regroupement est fait sur une valeur numérique ou une date.

## Onglets

Un des objectifs principaux de Panoptic est de permettre plusieurs façons d'explorer un corpus d'images simultanément. Pour cela, les onglets sont utilisés comme espaces de travail distincts, chacun pouvant avoir ses propres filtres, tris, groupes, vues et propriétés affichées.

## Vecteurs

Pour permettre l'utilisation d'algorithmes d'apprentissage automatique, les images sont transformées en **vecteurs** (ou **embeddings**) lors de leur importation dans Panoptic. Un vecteur est une liste de nombres représentant des **caractéristiques** de l’image.

Ces caractéristiques ne sont pas forcément interprétables directement, mais elles permettent de comparer les images entre elles. Par exemple, deux images de chats auront des vecteurs plus proches que ceux d'un chien.

## Clusters

Une fois les vecteurs calculés, les images peuvent être **regroupées automatiquement** en clusters. Contrairement aux groupes créés avec des propriétés, les clusters sont **paramétrables**, peuvent être générés avec différents algorithmes, et ne sont pas **déterministes** (un même clustering peut produire des résultats légèrement différents selon les exécutions).

## Similarité

Une fois les vecteurs calculés, la similarité entre images peut être mesurée. Différents algorithmes peuvent être utilisés. Panoptic utilise par défaut la **similarité cosinus**, dont les valeurs sont comprises entre **0 et 1**.

## Exécuter

Les calculs qui ne sont pas listés ci-dessus peuvent être lancés avec le bouton **"Exécuter"**, qui regroupe toutes les actions fournies par les plugins. Exemples :

- Détecter les couleurs principales des images et les enregistrer en tant que propriété.
- Exécuter l'OCR sur les images.
- Identifier les sujets principaux des textes associés aux images.
- Extraire des objets des images.

## Plugins

Les plugins permettent d'ajouter de nouvelles fonctionnalités à Panoptic. Chaque projet peut activer uniquement les plugins nécessaires, ce qui optimise la légèreté du logiciel. Même les fonctionnalités de deep learning de Panoptic sont intégrées sous forme de plugin.

Les plugins peuvent ajouter de nouvelles possibilités pour :

- Créer des clusters.
- Calculer des similarités.
- Ajouter des actions spécifiques via le bouton **"Exécuter"**.
