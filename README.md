# Parameter Store Manager

Are you tired of the AWS Console yet? Can't figure out `name` `starts-with` vs `path` `recursive` when searching for parameters?

#### Parameter Store Manager is a desktop application that helps users easily view/search/manage AWS parameter store parameters.

![alt text](https://raw.githubusercontent.com/smblee/parameter-store-manager/master/resources/screenshot.png)

Built with `electron-react-boilerplate`.

## Quick Start
- Download the binary here (Supports Windows, MacOS, Linux): https://github.com/smblee/parameter-store-manager/releases
- Make sure you have AWS Credentials set up on your machine (there are several ways to do this. E.g. `~/.aws/credentials` method) https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html
- Run the downloaded binary!

## Current Features

- View parameters: Tree view, list view
- Filter parameters: Filter by keyword (with highlighting)
- Search parameters: by path (glob (\*, \*\*) supported)
  - e.g. `/path/**/*Url`
  - e.g. `*parameter`
- Add new parameters
  - Service parameter (assuming path `/services/{environments}/{serviceName}/{parameterName}`)
  - Generic parameter
  - Supports `String`, `SecureString` (no `StringList` support atm)
    - Supports KMS Key Encryption for `SecureString`
- Edit parameter
  - Change the description, value
  - Change from/to `String` and `SecureString`
- Duplicate parameter
  - Opens the `add new parameters` flow with the values pre-filled.
- Delete parameter
- Copy parameter values with one click
- Refetch/refresh parameters
- Program Auto Updater/Update checker (Buggy?)

## Run

Start the app in the `dev` environment. This starts the renderer process in [**hot-module-replacement**](https://webpack.js.org/guides/hmr-react/) mode and starts a webpack dev server that sends hot updates to the renderer process:

```bash
$ yarn dev
```

If you don't need autofocus when your files was changed, then run `dev` with env `START_MINIMIZED=true`:

```bash
$ START_MINIMIZED=true yarn dev
```

## Packaging

To package apps for the local platform:

```bash
$ yarn package
```

To package apps for all platforms:

First, refer to the [Multi Platform Build docs](https://www.electron.build/multi-platform-build) for dependencies.

Then,

```bash
$ yarn package-all
```

To package apps with options:

```bash
$ yarn package --[option]
```

To run End-to-End Test

```bash
$ yarn build-e2e
$ yarn test-e2e

# Running e2e tests in a minimized window
$ START_MINIMIZED=true yarn build-e2e
$ yarn test-e2e
```

:bulb: You can debug your production build with devtools by simply setting the `DEBUG_PROD` env variable:

```bash
DEBUG_PROD=true yarn package
```

## CSS Modules

This boilerplate is configured to use [css-modules](https://github.com/css-modules/css-modules) out of the box.

All `.css` file extensions will use css-modules unless it has `.global.css`.

If you need global styles, stylesheets with `.global.css` will not go through the
css-modules loader. e.g. `app.global.css`

If you want to import global css libraries (like `bootstrap`), you can just write the following code in `.global.css`:

```css
@import '~bootstrap/dist/css/bootstrap.css';
```

## SASS support

If you want to use Sass in your app, you only need to import `.sass` files instead of `.css` once:

```js
import './app.global.scss';
```

## Static Type Checking

This project comes with Flow support out of the box! You can annotate your code with types, [get Flow errors as ESLint errors](https://github.com/amilajack/eslint-plugin-flowtype-errors), and get [type errors during runtime](https://github.com/codemix/flow-runtime) during development. Types are completely optional.

## TODOS

- Add app icon
- ~~Set up CI for release. (Windows, Mac, Linux)~~
- Clean up the code base and all the unneeded boilerplate code.
- ~~Create other releases besides Windows.~~
- Add tests
- Support other types of add use cases besides the assumed `services` pattern.
- Ability to view previous versions
- Logging
- Backup
- Autocomplete (service names)
- ~~Configure AWS Setup (Environments, etc.)~~
- Bulk delete
- Bulk edit

and a lot more...
