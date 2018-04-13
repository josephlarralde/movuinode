# Movuinode

## electron application for movuino sensors and more

#### getting started

* clone this repository.
* `cd` into it.
* type `npm install` to install dependencies.

Three `npm` scripts are available:

* `npm run watch` will build the application into the `dist` directory, start it, and watch modifications in the `assets` and `src` directories to rebuild and restart automatically.
* `npm run build` will build the application into the `dist` directory, and package it into the `build` directory using `electron-packager`.
* `npm run versions` will print a list of the versions of all `electron`'s dependencies (`node`, etc).

#### structure of this repository

* `assets` contains all the fonts and media used by the application.
* `bin` contains the build system, i.e. all the scripts used to transpile, render, and bundle the source code.
    * `bin/index.js` is the main entry point (see the `scripts` section in `package.json`).
    * `bin/config/default.js` contains all the information needed by the build system (some useful paths and the application's configuration).
* `src` is where all the source code is located:
    * `app` contains the es6 source code of the application.
    * `client` contains the es6 source code of the client pages served by the application's server.
    * `contents` contains some `markdown` files that will be rendered to `ejs` files.
    * `shared` contains some shared es6 source code.
    * `styles` contains the `sass` files that will be rendered to `css` files.
    * `views` contains some `ejs` files that will be copied to the `dist` directory.
* `dist` is where:
    * the fonts and media are copied from `assets`
    * the transformed code from `src`'s subdirectories is generated (for more info, have a look at `bin/config/default.js`).
    * the `package.json` file is copied.
    * a symbolic link to `node_modules` is created to allow `electron-packager` to do its job.
* `build` is where the actual applications are built using `electron-packager`, bundling the `dist` directory into a distributable software.

#### dependencies

This project uses:

* **`watch`** to watch for modifications in the `src` and `assets` directories and notify them.
* **`babel`** to transpile the es6 code from `src/app`, `src/client` and `src/shared` into `dist/app`, `dist/client` and `dist/shared`, respectively.
* **`browserify`** to bundle the transpiled code from `dist/client` and `dist/shared` into `dist/public/js` (to be served by the application's server).
* **`node-sass`** to render the `scss` files from `src/styles` to `css` files in `dist/public/css`.
* **`marked`** and `mustache` to allow writing comprehensive `markdown` files in `src/contents` and translate them to `ejs` in `dist/contents`.
* **`ejs`** to render the application's `html` interface and the `html` pages served by its server.
* **`express`** to make running a local server from the application easy.
* **`electron`** to run the application while developing.
* **`electron-packager`** to bundle the application into a distributable software.
