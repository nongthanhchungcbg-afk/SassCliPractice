# Sass npm & CLI Practice

A small responsive Sass practice project demonstrating Node.js/npm version checks, installing Sass as a project dependency, compiling SCSS with the Sass CLI, watch mode, and compiling multiple SCSS entry points.

The page demonstrates the compiled CSS. Sass partials share color tokens and mixins between the two entry points. `npm run build` compiles every `.scss` entry point in `scss/` to a matching `.css` file in `css/`; partials beginning with `_` are not emitted independently.

## Requirements and versions

Check that Node.js and npm are available:

```sh
node -v
npm -v
```

This exercise was checked with Node.js `v24.19.0`, npm `11.17.0`, and Dart Sass `1.105.1`. Other compatible Node.js releases can work too.

## Install Sass with npm

From this project folder, install its Sass development dependency:

```sh
npm install
npx sass --version
```

The global CLI version can also be checked with `sass --version`. For a one-off global install, Sass can instead be installed with `npm install --global sass`; the project itself uses the local npm dependency so collaborators can reproduce the same compiler version.

## Compile SCSS to CSS

Compile both entry points in one command:

```sh
npm run build
```

Or compile the whole directory directly with Sass CLI:

```sh
npx sass --no-source-map scss:css
```

Compile one file at a time if needed:

```sh
npm run build:main
npm run build:cards
```

The source files `scss/main.scss` and `scss/cards.scss` produce `css/main.css` and `css/cards.css`.

## Watch for changes

Start the watcher and leave this terminal open:

```sh
npm run watch
```

This runs the equivalent Sass CLI command:

```sh
npx sass --no-source-map --watch scss:css
```

Save an SCSS file to have Sass recompile the affected CSS automatically. Press `Ctrl+C` to stop watching.

## Windows PowerShell note

If PowerShell blocks the `npm.ps1` shim with an execution-policy error, run the Windows command shim instead, for example `npm.cmd install` or `npm.cmd run build`. This avoids weakening the machine-wide PowerShell execution policy. If you need Sass without Node/npm, use the standalone Dart Sass archive from the [official Sass releases](https://github.com/sass/dart-sass/releases).

## Open the demo

Open `index.html` in a browser. The project uses local compiled CSS and does not need a build server.
