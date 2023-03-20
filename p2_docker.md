
1. docker volume volumenDocker



2. docker run -d -p 8080:80 --name nginx1 -v /home/poo/Escritorio/docker/mi-apache:/usr/share/nginx/html nginx



3. dockerfile dsp de crear la imagen 

FROM nginx

COPY   ./index.html /usr/share/nginx/html/

cambiar el contenido del index.html de la carpeta mi-apache


4.  crear un nuevo directorio dentro de mi-apache y copiar el index.html con     diferente contenido
    
    docker run -d -p 8081:80 --name nginx2 -v /home/poo/Escritorio/docker/mi-apache/nginx2-index:/usr/share/nginx/html nginx



5. http://localhost:8080/
    http://localhost:8081/

## parte 2

1. docker network create redDocker

2. docker run --name Ubuntu1 -it ubuntu

3. docker run --name Ubuntu2 -it ubuntu


4. docker network connect redDocker Ubuntu1
 

5.  Al intentar hacer ping a Ubuntu1 desde Ubuntu2, probableente no funciona ya que los contenedores no están conectados a la misma red y no se pueden comunicar directamente.

6. docker network connect redDocker Ubuntu2

7. ping Ubuntu1
