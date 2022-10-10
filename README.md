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


