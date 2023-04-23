# Ejercicio: práctica 1

Crear un contenedor con Apache Server. El servidor por defecto muestra en la página principal “It works!”. Modificar este mensaje para que muestre un saludo personal: “Hello + (tu nombre y apellidos)!”. Posteriormente, configurarlo para que por defecto utilice el puerto 8082.

Tareas:

1. Crear contenedor con Apache Server 2 (buscar en Docker Hub)

Para crear un contenedor nos basta con introducir en la terminal de nuestro sistema Linux lo siguiente:
```
#se buscan las imagenes disponibles de apache con este comando 
docker search apache2

#para conseguir la imagen oficial de apache se introduce
docker pull httpd

#ejecutamos el siguiente comando para crear un contenedor a partir de ella. Esto inicia un contenedor en modo de segundo plano (-d), redirige el puerto 80 de tu equipo al puerto 80 del contenedor (-p 80:80) y utiliza la imagen httpd que acabas de descargar.
docker run -d -p 80:80 httpd

#para comprobar que el contenedor ha sido creado, miramos con el siguiente comando en la columna 'CONTAINER_ID' y miramos si concuerda con el nombre que se asigno con el comando anterior
docker ps

#para ver los contenedores en ejecución, abrimos en el navegador y ponemos el siguiente comando, y comprobamos que hay un mensaje que diga 'It works!'
http://localhost

```
2. Personalizar el contenedor. 

Como lo que queremos es personalizar un contenedor deberemos de crear un documento *Dockerfile*. El archivo especifica qué sistema operativo base se utilizará, qué paquetes y aplicaciones se instalarán, qué puertos se expondrán, etc.

Sin el archivo Dockerfile, no habría forma de crear una imagen de contenedor de Docker personalizada que contenga un servidor web Apache en un contenedor de Ubuntu. donde introduciremos En el tendremos los siguientes comandos:\
```bash
FROM ubuntu:latest

#Actualizar el sistema y descargar Apache2
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y apache2 \
    && rm -rf /var/lib/apt/lists/*

#Copiar el archivo index.html a la carpeta de documentos de Apache2
COPY index.html /var/www/html/

#Exponer el puerto 80 para que el servidor web sea accesible desde el exterior
EXPOSE 80

#Iniciar el servicio de Apache2
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```
3. Subir la imagen del contenedor creado a Docker Hub. La imagen debe llamarse 
`apacheserver_p1`.

Creamos un *index.html* para para que muestre el mensaje pedido, dentro de dicho archivo introducimos:
```html
<h1> Hello Violeta Ai Naharro Zaldivar! <h1>
````

Para enlazar una imagen de Docker a Docker Hub, sigue los siguientes pasos:
```bash
#Creamos la imagen con:
docker build -t apacheserver_p1 

#Inicia sesión en Docker Hub:
docker login

#Se taggea la imagen que quieres subir con el nombre de tu repositorio en Docker Hub:
docker tag apacheserver_p1 ateloiv/apacheserver_p1

#Subimos la imagen taggeada a Docker Hub:

docker push ateloiv/apacheserver_p1
```

4. Subir el enlace de la imagen creada a la tarea del CV.

El enlace de la imagen se encuentra en mi cuenta:

[Haz click aquí](https://hub.docker.com/repository/docker/ateloiv/apacheserver_p1/general)
