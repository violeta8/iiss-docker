# PRÁCTICA 3

## tarea 1

1. Para componer un archivo docker-compose.yml, se debe tener en cuenta que este archivo debe tener la siguiente estructura:
```yml
version: '3.9'

services:
  db:
    image: mysql:5.7
    container_name: my_mysql_db
    environment:
      MYSQL_DATABASE: my_database
      MYSQL_USER: my_user
      MYSQL_PASSWORD: my_password
      MYSQL_ROOT_PASSWORD: my_root_password
    volumes:
      - mysql_data:/var/lib/mysql

  drupal:
    image: drupal:9.2.0-apache
    container_name: my_drupal
    ports:
      - "8080:80"
    environment:
      DRUPAL_DATABASE_HOST: db
      DRUPAL_DATABASE_PORT: '3306'
      DRUPAL_DATABASE_NAME: my_database
      DRUPAL_DATABASE_USER: my_user
      DRUPAL_DATABASE_PASSWORD: my_password
    volumes:
      - drupal_data:/var/www/html
    depends_on:
      - db

volumes:
  mysql_data:
  drupal_data:

```
Se ha creado un archivo llamado Docker-compose.yml utilizando el comando nano, donde se han definido dos servicios: drupal y MySQL. Cada servicio tiene una imagen y un nombre de contenedor específicos, y el servicio MySQL requiere un archivo de variables de entorno para su correcto funcionamiento. El servicio de drupal se ha configurado para usar el puerto 81 y ambos servicios tienen configurado un volumen. A pesar de esto, el proyecto no se ha completado con éxito debido a un error que aparece después de realizar varios cambios.


## tarea 2

```yml
version: '3'

services:
  db:
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
      MYSQL_ROOT_PASSWORD: root
    volumes:
      - db_data:/var/lib/mysql

  wordpress:
    depends_on:
      - db
    image: wordpress
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wp_data:/var/www/html

volumes:
  db_data:
  wp_data:
```

El Docker Compose anterior define dos servicios: un contenedor de base de datos MariaDB y un contenedor de WordPress. Ambos servicios se conectan a una red personalizada llamada "redDocker", lo que les permite comunicarse entre sí. Al usar Docker Compose, se pueden administrar fácilmente los servicios y los volúmenes relacionados en una sola configuración en lugar de ejecutar los contenedores manualmente y tener que establecer manualmente las conexiones y configuraciones cada vez.