
# PRÁCTICA 2: DOCKER

## Parte 1

1. docker volume volumenDocker

Este comando crea un volumen llamado volumenDocker. Los volúmenes son directorios que se crean en el sistema de archivos del host y que se pueden montar en los contenedores. Los volúmenes son útiles para compartir datos entre contenedores y entre contenedores y el host. Los volúmenes también son útiles para persistir datos de contenedores que se eliminan. Los volúmenes se crean en el directorio /var/lib/docker/volumes/ en el host. Los volúmenes se pueden crear de forma explícita con el comando docker volume create o de forma implícita al crear un contenedor con el parámetro -v.

2. docker run -d -p 8080:80 --name nginx1 -v /home/poo/Escritorio/docker/mi-apache:/usr/share/nginx/html nginx

Con este comando, se crea un contenedor llamado nginx1, que se ejecuta en segundo plano, que se conecta al puerto 8080 del host y que monta el volumen volumenDocker en el directorio /usr/share/nginx/html del contenedor. El contenedor se crea a partir de la imagen ng


3. dockerfile dsp de crear la imagen 

FROM nginx

COPY   ./index.html /usr/share/nginx/html/

Este archivo, cambia el contenido del index.html de la carpeta mi-apache

El dockerfile se encuentra en la carpeta mi-apache y se ejecuta el comando 'docker build -t nginx2 .' para crear la imagen nginx2

4.  crear un nuevo directorio dentro de mi-apache y copiar el index.html con     diferente contenido
    
    docker run -d -p 8081:80 --name nginx2 -v /home/poo/Escritorio/docker/P2/nginx2-index:/usr/share/nginx/html nginx



5. http://localhost:8080/
    http://localhost:8081/

    ![docker_p2](https://user-images.githubusercontent.com/117084676/233868530-6e231a86-a61a-4ffc-8bd9-e758970a14c6.jpg)


## Parte 2

1. docker network create redDocker

Este comando crea una red llamada redDocker. Las redes son espacios lógicos que permiten que los contenedores se comuniquen entre sí. Las redes se crean en el directorio /var/lib/docker/networks/ en el host. Las redes se pueden crear de forma explícita con el comando docker network create o de forma implícita al crear un contenedor con el parámetro --network.

2. docker run --name Ubuntu1 -it ubuntu

Este comando crea un contenedor llamado Ubuntu1, que se ejecuta en primer plano

3. docker run --name Ubuntu2 -it ubuntu

Este comando crea un contenedor llamado Ubuntu2, que se ejecuta en primer plano

4. docker network connect redDocker Ubuntu1

Con este comando se conecta el contenedor Ubuntu1 a la red "redDocker".

5.  Al intentar hacer ping a Ubuntu1 desde Ubuntu2, probableente no funciona ya que los contenedores no están conectados a la misma red y no se pueden comunicar directamente.

6. docker network connect redDocker Ubuntu2

Con este comando se conecta el contenedor Ubuntu2 a la red "redDocker".

7. ping Ubuntu1

Este comando permite hacer ping a Ubuntu1 desde Ubuntu2.
