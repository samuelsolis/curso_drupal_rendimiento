# Drupal stack sobre Docker

Este repositorio está basado en [Docker4Drupal](https://github.com/wodby/docker4drupal) y elaborado expresamente
para el curso de Rendimiento en Drupal de Udemy, elaborado por Samuel Solís.

El curso está íntegramente en castellano, por lo que toda la documentación estará en este idioma.


Docker4Drupal es un conjunto de máquinas docker administradas en con docker-compose. Utiliza el fichero docker-compose.yml para personalizar las máquinas virtuales de docker.

- Lea la documentación para más información sobre [cómo usarlo](https://wodby.com/docs/stacks/drupal/local#usage).
- Puedes preguntar en [Slack](http://slack.wodby.com/) tus dudas y sugerencias.
- Sigue a [@wodbycloud](https://twitter.com/wodbycloud) para estar al tanto de todas las novedades.


## Stack

En el curso (y en este repositorio) trabajaremos con las siguientes imágenes.

| Container       | Versions               | Service name    | Image                              | Default |
| --------------  | ---------------------- | --------------- | ---------------------------------- | ------- |
| [Apache]        | 2.4                    | `apache`        | [wodby/apache]                     |         |
| [Drupal]        | 9, 8, 7                | `php`           | [wodby/drupal]                     | ✓       |
| [PHP]           | 8.0, 7.4, 7.3          | `php`           | [wodby/drupal-php]                 |         |
| [MariaDB]       | 10.5, 10.4, 10.3, 10.2 | `mariadb`       | [wodby/mariadb]                    | ✓       |
| [Redis]         | 6, 5                   | `redis`         | [wodby/redis]                      |         |
| [Varnish]       | 6.0, 4.1               | `varnish`       | [wodby/varnish]                    |         |
| [Node.js]       | 14, 12, 10             | `node`          | [wodby/node]                       |         |
| [Drupal node]   | 1.0                    | `drupal-node`   | [wodby/drupal-node]                |         |
| [Xhprof viewer] | latest                 | `xhprof`        | [wodby/xhprof]                     |         |
| phpMyAdmin      | latest                 | `pma`           | [phpmyadmin/phpmyadmin]            |         |
| Portainer       | latest                 | `portainer`     | [portainer/portainer]              | ✓       |
| Traefik         | latest                 | `traefik`       | [_/traefik]                        | ✓       |

Versiones de Drupal óptimas para el curso: 9 / 8

## Documentation

Toda la documentación sobre este docker-compose y su uso está en https://wodby.com/docs/stacks/drupal/local.

## Cómo instalar Drupal utilizando este repositorio.
1. Duplica el fichero .env.example y renómbralo como .env
2. Este será tu fichero de configuración, podrás cambiarlo a tu antojo.
3. Instala Docker ([Linux](https://docs.docker.com/engine/installation), [Docker for Mac](https://docs.docker.com/engine/installation/mac) or [Docker for Windows (10+ Pro)](https://docs.docker.com/engine/installation/windows))
4. Para linux, adicionalmente instala [Docker Compose](https://docs.docker.com/compose/install)
5. Ejecuta el comando `docker-compose up -d` 
6. Accede al contenedor php para instalar drupal con el comando `docker-compose exec php bash`
7. Una vez dentro, ejecuta el comando `composer install` que obtendrá los ficheros de Drupal.
8. Puedes salir del contenedor escribiendo `exit`
9. Añade a tu fichero de hosts la linea `127.0.0.1 drupal.docker.localhost`. Cambia el dominio si lo has cambiado en el ".env". Este paso puede no ser necesario, algunos navegadores como Chrome ya detectan esta url.
10. En la url `drupal.docker.localhost` deberás tener disponible Drupal listo para instalar, con el wizard de instalación.