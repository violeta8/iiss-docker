# PRÁCTICA 3

## tarea 1

1. Para componer un archivo docker-compose.yml, se debe tener en cuenta que este archivo debe tener la siguiente estructura:
```yml
version: "3"

services:
mysql:
image: mysql:8.0
container_nane: mysql
env_file:—.env
volumes:
- volumenbockerC:/var/Lib/mysql

drupal:
image: drupal:8.7.8-fpm-alpine
container_name: drupal

ports:

- 81:5000

volumes:

- volumenbockerC:/var /ww/htmt

volumes:
volumenDockerC:
```
Se ha creado un archivo llamado Docker-compose.yml utilizando el comando nano, donde se han definido dos servicios: drupal y MySQL. Cada servicio tiene una imagen y un nombre de contenedor específicos, y el servicio MySQL requiere un archivo de variables de entorno para su correcto funcionamiento. El servicio de drupal se ha configurado para usar el puerto 81 y ambos servicios tienen configurado un volumen. A pesar de esto, el proyecto no se ha completado con éxito debido a un error que aparece después de realizar varios cambios.


## tarea 2

1. 
2. 
3. 
4. 