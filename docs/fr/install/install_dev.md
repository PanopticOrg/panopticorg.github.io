# Installation (développement)

Si vous souhaitez contribuer à panoptic en modifiant le code ou en développant des plugins vous aurez besoin de pouvoir faire tourner panoptic en mode développement.

Commencez par cloner le repository avec: 

```sh
git clone https://github.com/CERES-Sorbonne/Panoptic.git
``` 

## Développement backend uniquement

Pour tester et modifier le fonctionnement backend, nous fournissons un front-end déjà buildé dans le dossier html du back:

* aller dans le dossier `panoptic-back`
* pour installer les dépendances:
```sh
pip install -e .
```
* lancer:
 ```sh
 panoptic
 ```


## Développement front et back

1. réaliser tout d'abord les étapes d'installation du backend
2. aller dans le dossier `panoptic-front`
3. lancer `npm install`
4. lancer `npm run dev`
5. avant de lancer le backend la variable d'environnement `PANOPTIC_ENV` devra être set à `DEV` afin d'utiliser le frontend de développement.