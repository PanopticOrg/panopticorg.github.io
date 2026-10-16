## Liste des plugins existants

Ci-dessous sont listés brièvement les plugins (autre que le plugin de similarité), pour plus de détails, cliquer sur le lien:

- [PanopticOCR](https://github.com/PanopticOrg/PanopticOCR): Utilisation de DOCtr pour réaliser de l'OCR sur les images sélectionnées, les résultats sont loin d'être parfaits, mais permettent de faire une recherche approximative dans les propriétés textes créées par le plugin.
- [PanopticColor](https://github.com/PanopticOrg/PanopticColor): Calculs des valeurs de teinte, saturation, valeur, luminosité ainsi que rouge, bleu et vert des images, permettant de manipuler par la suite les images grâce à leurs propriétés colorimétriques.
- [PanopticText](https://github.com/PanopticOrg/PanopticText): Regroupe, compare, recherche et cartographie les images selon une propriété texte (OCR, transcription, légende...), voir [le détail ci-dessous](#panoptictext).
- [PanopticMATCH](https://github.com/PanopticOrg/PanopticMatch): Pour chaque image d'un dossier, trouve l'image la plus similaire d'un autre dossier (par exemple pour retrouver l'original d'une image retouchée), à partir de vecteurs déjà calculés. Les paires sont affichées par similarité décroissante.

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
