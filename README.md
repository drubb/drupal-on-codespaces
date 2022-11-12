# Drupal on Codespaces

This project enables running Drupal projects on Github Codespaces, providing a customized container environment
and adding some useful VSCode extensions and settings.

## Quickstart

* Open this project in Codespaces
* Open the terminal
* Create a Drupal project: `composer create-project drupal/recommended-project <myfolder>`
* Enter the created folder: `cd <myfolder>`
* Add Drush: `composer require drush/drush`
* Start the Drupal installation: `drush si` - specify **sqlite** as Database driver, defaults otherwise!
* Optional: Change the admin password: `drush upwd admin <password>`
* Optional: Generate initial support for services code completion (see below): `drush generate phpstorm-metadata`
* Run the development server: `drush serve`

## Basic Docker image

This project is based on Debian's stable Bullseye image (Debian 11). I've added some cli tools, php extensions
required for Drupal, and also nodejs (LTS), npm and the Drupal Drush launcher for convenience. Take a look at devcontainer/Dockerfile to find out more.

## VSCode extensions and settings

I've added some basic extensions and settings to support code completion and specific Drupal requirements.
Take a look at .devcontainer/devcontainer.json for details.

## Code completion for Drupal development

While VSCode isn't as well suited for Drupal PHP development like e.g. PhpStorm, at least basic support for Drupal
features can be achived using various extensions. For now the following should work:

* Suggestions for Drupal Hooks: typing **hook_** in your .module files reveals a list of Drupal Hooks. Select one and
you'll get the code snippet for your file, including docblock and function arguments.
* Autocompletion for service identifiers: `\Drupal::service('')` provides a list of Drupal service ids, like e.g. 'entity_type.manager'. Should also work for `$container->get('')`. If it doesn't, please press F1 and run the 'Drupal Intellisense:Scan Workspace' command in VSCode.
* Suggestions for Drupal service methods: supplied by PHP Intelephense extension, with the help of [PhpStorm Metadata](https://www.jetbrains.com/help/phpstorm/ide-advanced-metadata.html). To use this you need to generate the data using Drush: `drush generate phpstorm-metadata`. Repeat this whenever your services change,
e.g. by installing contributed modules or writing custom services.
* Autocompletion and Emmet support for Twig files.

## Licence: MIT
