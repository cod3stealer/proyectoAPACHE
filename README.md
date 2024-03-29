# proyectoAPACHE

Lo primero es crear la carpeta que contendrá todo lo que se quiera hacer.
Mi carpeta "server" contiene las carpetas "sitio1, sitio2, sitio HTTPS y sitioSSL". 

Ahora que está todo ordenado, busco la imagen de apache-php en hub.cokcer.com 
y configuro el **docker-compose.yml** para definir al contenedor.

Por otro lado, también contiene los archivos docker-compose.yml (el cual creo de manera manual 
igual que los demás archivos), info.php, README.md

Dentro del docker-compose.yml declaro el contenedor con su imagen, puerto y volumenes

```
version: "3.3"
services:
 apache-XD:
  container_name: apache-XD
  image: php:7.2-apache
  ports:
    - "80:80"
  volumes:
    - /home/asir2a/Escritorio/SRI/tuto/server:/var/www/html
    - configApache:/etc/apache2
volumes:
  configApache:
```
En ~/server/info.php pongo: 
```
<?php
    phpinfo();
?>
```
Una vez esto está hecho, dentro de sitio1/ creo un archivo llamado index.html en el cual pongo `<h1>hola mundo</h1>`
Ahora lo que hago es ejecutar docker-compose up y en el navegador buscar **localhost:80**

En este localhost/sitio1 aparece por pantalla <h1>hola mundo</h1>

![hola mundo: ](cap/a.png)

Por otro lado, en localhost/info.php debería aparecer una tabla de información con toda la sálida de la función `phpinfo()`

# Mapeo del Documento Root

Para mapear este documento, hay que hacer un volumen asociado al root en la configuración
del documento docker-compose.yml

```
version: "3.3"
services:
 apache-XD:
  container_name: apache-XD
  image: php:7.2-apache
  ports:
    - "80:80"
  volumes:
    - /home/asir2a/Escritorio/SRI/tuto/server:/var/www/html
  **- configApache:/etc/apache2**
volumes:
 **configApache:**
```
Lo próximo que se debe hacer es ir al apartado de volúmenes del VCode y seleccionar server_configApache con el clic derecho y abrirno en un Dev Container.
Una vez allí, se puede descargar toda la configuración necesaria a la carpeta del server si así se quiere.


# Primeros intentos de Mermaid, práctica de COD // DAM1
## Diagrama Simple
```
graph TD;
 A-->B;
 B-->C;
 C-->D;
 C-->E;
```

## Flowchart
```
flowchart LR

A[Cuadrado entre corchete] -->|texto entre medios va entre palos| B(Circulao entre parentesis)
B --> C{Decision va entre llaves}
C -->|C puede ir a Resultado 1| D[Resultado 1]
C -->|o C puede ir a Resultado 2| E[Resultado 2]
```

Prueba con ejemplo de un código `a++;print(a);`
```
flowchart LR

A[variable a = 0] -->|suma unitaria| B(print(a))
B --> C[Resultado final = 1]
```

## Prueba con diagrama secuencial
```
sequenceDiagram
Santi->>Damian: Damian, ponme una buena nota porfa
Note right of Santi: vamo a ve si me pone diez
Damian-->>Santi: venga va
Santi->>Damian: viva messi
```


