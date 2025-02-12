# Installation (développement)

Les étapes suivantes impliquent d'avoir cloné le répertoire et sont recommandées pour les utilisateurs souhaitant avoir accès aux versions de développement, ou souhaitant modifier eux même le code afin de contribuer.

## Développement backend uniquement

Pour tester et modifier le fonctionnement backend, nous fournissons un front-end déjà buildé dans le dossier html du back.
* aller dans le dossier `panoptic-back`
* pour installer les dépendances
    - `python3 setup.py install` simplement pour utiliser panoptic
    - `pip3 install -e .` pour développer
    - `pip3 install -r requirements.txt` et il faut ajouter `panoptic-back` au PYTHON_PATH également pour développer
* lancer `python panoptic/main.py`


## Développement front et back

1. réaliser tout d'abord les étapes d'installation du backend
2. aller dans le dossier `panoptic-front`
3. lancer `npm install`
4. lancer `npm run dev`
5. avant de lancer le backend la variable d'environnement `PANOPTIC_ENV` devra être set à `DEV` afin d'utiliser le frontend de développement.