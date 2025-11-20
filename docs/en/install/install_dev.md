# Installation (Development)

If you wish to contribute to Panoptic by modifying the code or developing plugins, you will need to be able to run Panoptic in development mode.

Start by cloning the repository with:

```sh
git clone https://github.com/CERES-Sorbonne/Panoptic.git
```

## Backend Development Only

To test and modify the backend functionality, we provide an already built front-end in the backend's html folder:

* go to the `panoptic-back` folder
* to install dependencies:
```sh
pip install -e .
```
* launch:
 ```sh
 panoptic
 ```


## Front-end and Back-end Development

1. first, complete the backend installation steps
2. go to the `panoptic-front` folder
3. run `npm install`
4. run `npm run dev`
5. before launching the backend, the `PANOPTIC_ENV` environment variable must be set to `DEV` to use the development frontend.