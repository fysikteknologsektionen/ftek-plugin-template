# ftek-plugin-template

A template for WordPress plugins.

## Dependencies

-   PHP (^7.4.x)
-   WordPress (>=5.9.x)

## Contributing

### VS Code

This project is set up for development with the editor/IDE [VS Code](https://code.visualstudio.com/). It is strongly recommended that you use this editor.

### Devcontainer

The project includes a [devcontainer](https://code.visualstudio.com/docs/remote/create-dev-container) configuration which contains all tools needed for development. To use this you need to install Docker (either CLI or [Docker Desktop](https://www.docker.com/products/docker-desktop/)), and the [remote development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) after which you can simply select "Clone Repository in Container Volume..." from the Remote Explorer tab.

After starting the devcontainer, WordPress will be accessable at <http://localhost:8888> on your local machine. After installing composer and npm dependencies and building javascript files (see [Getting Started](#getting-started)) you may log in to WordPress and activate your plugin. To log in, visit <http://localhost:8888/wp-login.php> and entering the default credentials:

-   Username: `admin`
-   Password: `password`

### Getting started

Before continuing you must install npm and Composer dependencies:

```console
npm install
composer install
```

During development, the following command will automatically rebuild code as source files are changed.

```console
npm run start
```

You should check for (stylistic) errors in your code by running

```console
npm run lint
```

Format the code base by running

```console
npm run format
```

Create a production build by running

```console
npm run build
```

For simplicity when installing the plugin, we keep built files under version control. Lint, format and build your code before commiting any changes.

### Visual Studio Code

If you encoder unexpected TypeScript errors in Visual Studio Code, make sure to [use the workspace version of TypeScript](https://code.visualstudio.com/docs/typescript/typescript-compiling#_using-the-workspace-version-of-typescript).

### Generate autoload files

To import PHP classes, we use the [autoload file generated by Composer](https://getcomposer.org/doc/01-basic-usage.md#autoloading). After creating a new file containing a class you would like to import, regenerate the autoload file by running

```console
composer dump-autoload
```

### Internationalization

Run the command

```console
npm run i18n
```

to scan the source code for translatable strings (which are stored in a POT file inside the `languages` folder) and update existing translations (PO files also stored inside `languages`) from the POT file. To edit an existing localization, edit the corresponding PO file. To create a new localization, copy the POT file to a new PO file inside `languages`. Assuming the POT file is named `my-text-domain.pot`, name the PO file `my-text-domain-{locale}.po`, for example `my-text-domain-en_US.po`. Lists of locale codes available in WordPress can be found [online](https://wpastra.com/docs/complete-list-wordpress-locale-codes/).

## Releases

[GitHub Actions](https://github.com/features/actions) is configured to automatically create a new release when a new [tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging) is pushed. Some useful commands are

```console
git tag                 # Lists existing tags
git tag -a vx.x.x       # Creates a new tag for the specified version number
git push --follow-tags  # Pushes commits and tags to the remote
```
