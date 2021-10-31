# Drupal on Codespaces

This project enables running Drupal projects on Github Codespaces, providing a customized container environment
and adding some useful VSCode extensions and settings.

## Quickstart

* Open this project in Codespaces
* Open the terminal
* Create a Drupal project: `composer create-project drupal/recommended-project <myfolder>
* Enter the created folder: `cd <myfolder>`
* Add Drush: `composer require drush/drush`
* Start the Drupal installation: `drush si` - specify **sqlite** as Database driver, defaults otherwise!
* Optional: Change the admin password: `drush upwd admin <password>`
* Run the development server: `drush serve`

## Basic Docker image

This project is based on the excellent PHP Docker image provided by [Wodby](https://github.com/Wodby). You'll get all PHP extensions
usually required to run Drupal projects, even ImageMagick.
I've added nodejs, npm and the Drupal Drush launcher for convenience. Take a look at .devcontainer/Dockerfile to find out more.

## VSCode extensions and settings

I've added some basic extensions and settings to support code completion and specific Drupal requirements.
Take a look at .devcontainer/devcontainer.json to find out more.

## Licence: MIT
