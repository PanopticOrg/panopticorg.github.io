## Liste des plugins existants

Ci-dessous sont listés brièvement les plugins (autre que le plugin de similarité), pour plus de détails, cliquer sur le lien:

- [PanopticOCR](https://github.com/PanopticOrg/PanopticOCR): Utilisation de DOCtr pour réaliser de l'OCR sur les images sélectionnées, les résultats sont loin d'être parfaits, mais permettent de faire une recherche approximative dans les propriétés textes créées par le plugin.
- [PanopticDescribe](https://github.com/PanopticOrg/PanopticDescribe): Décrit en langage naturel le contenu des images sélectionnées et l'enregistre dans une propriété texte, pour pouvoir ensuite rechercher, filtrer ou regrouper les images selon leur contenu, voir [le détail ci-dessous](#panopticdescribe).
- [PanopticColor](https://github.com/PanopticOrg/PanopticColor): Calculs des valeurs de teinte, saturation, valeur, luminosité ainsi que rouge, bleu et vert des images, permettant de manipuler par la suite les images grâce à leurs propriétés colorimétriques.
- [PanopticText](https://github.com/PanopticOrg/PanopticText): Regroupe, compare, recherche et cartographie les images selon une propriété texte (OCR, transcription, légende...), voir [le détail ci-dessous](#panoptictext).
- [PanopticMATCH](https://github.com/PanopticOrg/PanopticMatch): Pour chaque image d'un dossier, trouve l'image la plus similaire d'un autre dossier (par exemple pour retrouver l'original d'une image retouchée), à partir de vecteurs déjà calculés. Les paires sont affichées par similarité décroissante.

## PanopticDescribe

PanopticDescribe génère une description de chaque image avec un modèle d'IA exécuté en local : aucune image n'est envoyée sur internet. La fonction `describe` s'applique aux images sélectionnées, ou à tout le projet si aucune image n'est sélectionnée, et remplit la propriété texte `description` (nom modifiable dans les paramètres du plugin). Les images déjà décrites sont ignorées, sauf si l'option `overwrite` est cochée. Le modèle est téléchargé à la première utilisation.

Deux moteurs sont disponibles dans les paramètres du plugin (`engine`) :

- `florence2` (par défaut) : rapide, fonctionne sans carte graphique, mais décrit uniquement en anglais. Le paramètre `detail` règle la longueur de la description : `short` (une ligne), `detailed` (deux ou trois phrases) ou `very_detailed` (un paragraphe).
- `vlm` : un modèle de langage multimodal (Qwen3.5) qui suit une consigne libre, le paramètre `prompt`, dans n'importe quelle langue : par exemple `Décris cette image en une phrase.` pour des descriptions en français, ou `Liste les objets visibles sur cette image, séparés par des virgules.` Les descriptions sont meilleures, mais plus lentes : une carte graphique est recommandée.

!!! note

    Les descriptions sont des propriétés texte comme les autres : on peut y faire une recherche, ou les utiliser avec PanopticText pour regrouper ou cartographier les images selon le sens de leur description.

## PanopticText

PanopticText travaille sur le texte associé aux images plutôt que sur les images elles-mêmes : il suffit d'avoir une propriété de type texte, remplie à la main, importée ou créée par un plugin comme PanopticOCR.

Il propose deux manières de rapprocher les textes :

- **par le vocabulaire** : deux textes sont proches s'ils emploient les mêmes mots. Aucun modèle n'est nécessaire, c'est rapide et adapté pour retrouver des documents d'un même type (actes, formulaires, lettres...).
- **par le sens** : deux textes sont proches s'ils parlent de la même chose, même avec des mots différents, ou dans des langues différentes. Cela demande de calculer d'abord des vecteurs de texte.

### Calculer les vecteurs de texte

Les vecteurs de texte se créent comme les vecteurs d'images (voir [Choisir son modèle](../advanced/models.md#creer-de-nouveaux-vecteurs)) : dans les paramètres du projet, Vecteurs > Ajouter un type de vecteur, on choisit la fonction `create_vector_type` de PanopticText, puis :

- `text_property` : la propriété texte à utiliser,
- `model` : le modèle, tous multilingues :
    - `multilingual_minilm` (par défaut) : le plus rapide, suffisant dans la plupart des cas,
    - `multilingual_mpnet` et `multilingual_e5` : meilleurs mais plus lents,
    - `bge_m3` : pour des textes longs, nettement plus lent, carte graphique recommandée,
- `custom_model` : optionnel, le nom de n'importe quel autre modèle [Hugging Face](https://huggingface.co/), qui remplace le choix précédent.

On obtient un type de vecteur par propriété et par modèle. Si des textes sont modifiés par la suite, seuls ceux-là sont recalculés : il suffit de relancer le calcul depuis la liste "Vecteurs disponibles", ou de lancer une des fonctions ci-dessous, qui le propose automatiquement.

!!! note

    Les textes longs (une page d'OCR par exemple) sont découpés en morceaux de la taille acceptée par le modèle, puis résumés en un seul vecteur. Comme les vecteurs sont attachés aux images, les instances d'une même image partagent un seul texte : leurs valeurs sont mises bout à bout.

### Les fonctions

Pour regrouper les images (vue "Groupée") :

- `cluster_text_syntax` : regroupe par vocabulaire, sans vecteurs. On choisit la propriété texte et le nombre de clusters. L'option `analyzer` permet de comparer des morceaux de mots (`characters`) plutôt que des mots entiers (`words`) : c'est plus tolérant aux erreurs d'OCR et aux variantes d'orthographe.
- `cluster_text_semantic` : regroupe par sens, à partir des vecteurs de texte. Avec un nombre de clusters à 0, le nombre de groupes est trouvé automatiquement et les textes qui ne ressemblent à aucun groupe sont mis à part dans un groupe "Outliers" ; `min_cluster_size` fixe alors la taille minimale d'un groupe.

Dans les deux cas, chaque groupe est nommé par ses mots les plus caractéristiques et reçoit un score de cohésion (de 0 à 1, plus il est élevé, plus les textes du groupe se ressemblent). En cochant `save_as_property`, chaque image reçoit son groupe dans une propriété tag "*nom de la propriété* clusters", pour pouvoir filtrer ou trier dessus sans relancer le calcul.

Les autres fonctions utilisent les vecteurs de texte :

- `find_similar_texts` : à partir des images sélectionnées, trouve les images dont le texte est le plus proche.
- `search_text` : recherche par le sens et non par les mots exacts. Elle est aussi disponible comme mode de la barre de recherche.
- `text_map` : crée une carte dans la vue spatiale où les images sont placées selon le sens de leur texte.

!!! note

    Les fonctions du plugin de similarité (PanopticML) n'utilisent que leurs propres vecteurs : les vecteurs de texte ne leur sont pas proposés.
