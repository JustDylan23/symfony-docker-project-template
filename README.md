# Symfony5 Docker Development Stack
This is a lightweight stack based on Alpine Linux for running Symfony5 into Docker containers using docker-compose. 

### Prerequisites
* [Docker](https://www.docker.com/)

I highly advice you to run docker on Linux since its really slow on Windows compared to linux. You can make use of WSL to run docker on Windows if you want good speeds. In this case I recommend that you also have your project files in your WSL else WSL won't do much for you since the reason why it is slow on Windows is due to transfer speeds between the Linux containers and Windows.

### Container
 - [nginx](https://hub.docker.com/_/nginx) 1.19.+
 - [php-fpm 8](https://hub.docker.com/_/php) php 8.0
    - [composer](https://getcomposer.org/) 
    - [yarn](https://yarnpkg.com/lang/en/) and [node.js](https://nodejs.org/en/) (if you will use [Encore](https://symfony.com/doc/current/frontend/encore/installation.html) for managing JS and CSS)
- [mysql](https://hub.docker.com/_/mysql/) 5.7.+
- [PhpMyAdmin](https://hub.docker.com/_/phpmyadmin)

### Included packages
- [symfony/skeleton](https://packagist.org/packages/symfony/skeleton) \
  The core of Symfony
- [symfony/orm-pack](https://packagist.org/packages/symfony/orm-pack) \
  The default ORM for Symfony
- [doctrine/doctrine-fixtures-bundle](https://packagist.org/packages/doctrine/doctrine-fixtures-bundle) \
  Used for populating the database with dummy data
- [symfony/validator](https://packagist.org/packages/symfony/validator) \
  Used to validate forms and entities
- [symfony/form](https://packagist.org/packages/symfony/form) \
  Used to dynamically generate html forms and integrates with validator and ORM
- [symfony/twig-pack](https://packagist.org/packages/symfony/twig-pack) \
  The default rendering engine of Symfony
- [symfony/debug-pack](https://packagist.org/packages/symfony/debug-pack) \
  Includes debug commands as well as a profiler and debug statements
- [symfony/security-bundle](https://packagist.org/packages/symfony/security-bundle) \
  Adds support for authentication and authorisation as well as making user entities and login forms
- [sensio/framework-extra-bundle](https://packagist.org/packages/sensio/framework-extra-bundle) \
  Allows the user to define routes and other things directly above the controller via annotations instead of in a dedicated yml file
- [symfony/maker-bundle](https://packagist.org/packages/symfony/maker-bundle) \
  Allows the user to generate code via the command like, for example entities, forms, login pages, etc.
- [symfony/webpack-encore-bundle](https://packagist.org/packages/symfony/webpack-encore-bundle) \
  Integrates your Symfony app with Webpack Encore!

All the bundles that make use of the Symfony flex recipe system can be found at https://flex.symfony.com/ 
you can simply add them by your project by using 
```
$ composer require reciple_name_or_package_bane
```

### Installing
Before running any of these commands you will want to make sure you configure the database name correctly in the following files:
- docker-compose.yml
- .env

starting the docker containers:
```
 docker-compose up -d
```
connecting to the docker container:
```
 docker-compose exec php sh
```
installing backend dependencies after connecting to the container for the first time
```
$ composer install
```
installing frontend dependencies
```
$ yarn
```
building frontend dependencies
```
$ yarn encore dev
```
building frontend dependencies + rebuilding on updates
```
$ yarn encore dev-server --hot
```

modify your DATABASE_URL config in .env 

### Ready up
open [localhost](http://localhost/) in your browser and you should see the default page configured by Symfony. There are some controller functions that you can uncomment in src/Controller/IndexController.php and play around with.
 
### Thanks to
https://github.com/mlocati/docker-php-extension-installer \
https://github.com/denji/nginx-tuning \
https://github.com/coloso/symfony-docker
