# Documentation

This is a `Drupal` website created for the course `R0330-3009` named `Web Content Management Systems` at `Laurea`. 

# Git

The application's code can be found in the following `Github` repository: [R0330-3009_1_drupal](https://github.com/zilahir/R0330-3009_1_drupal).

# Implementation

## Docker

This Drupal application is created using `Docker`, to combine all the related service a `Drupal` site needs.

These are: 

1) webserver (`nginx`)
2) database (`mysql with mariadb`)
3) drupal (using the official `drupal` docker image)
4) certbot (to create SSL cert on the nginx server)

The container's a combed together using `docker-compose`. The `docker-compose` file can be found [in this file](https://github.com/zilahir/R0330-3009_1_drupal/blob/master/docker-compose.yml). 

## Webserver

The webserver using a simple `nginx` webserver. The `nginx` config can be found in [this file](https://github.com/zilahir/R0330-3009_1_drupal/blob/master/nginx-conf/nginx.conf). 

_Usually_ the `nginx` webserver are listening on the `80` port by default. I do have something running on that port already, so I needed to configure the server to listen on a different port. I've decided to set it for `80`. 

Then, to able to open the service running on this port on the `host` machine, I am mapping the `81` port to the `3300`. This happens in the `docker-compose` file, defining in the `ports` directive:

```yml
    ports:
      - 3300:81
```

## Database

The database for this drupal application is using a default `mysql` instance. The `mysql` is also defined as a service in the `docker-compose` file, with the name of `mysql`, and using the `8.0` version of the official `mysql` `docker` image. 

The database related secrets are stored in an `env` file, which is given as an argument when defining the service. 

If you want to fire up this application on your own machine using docker, you need to do the following: 

1) create a .env file in your local clone of _this_ repository: 


```bash
touch .env
```

2) Open this file using any text editor of your choice, for example: 

```bash
vim .env
```

3) Add the following key with the value of choice:

```bash
MYSQL_ROOT_PASSWORD=
MYSQL_DATABASE=drupal
MYSQL_USER=
MYSQL_PASSWORD=
```

## Drupal

This application is using the `8.7.8` version of drupal built on the `fpm-alpine`. (`drupal:8.7.8-fpm-alpine`).


## Certbot

Issuing `SSL` certificate on the target domain when deployng a container drive web application. The deployment process is discussed later in this documentation.


# Requirements

* The drupal project comes with the following requirements: 
* Responsiveness 5 Points: •web site is  responsive •images are responsive
* Make use of different features (10 points):
    * Youtube Videos
    * contact form 
    * galleries & slideshows
    * map
* Visuality (20P):
    * Content
    * Theme selection
    * Typography
    * Logo 
    * Favicon 
* Functionality of navigation(10P)
* Over all appearance(5P) 

