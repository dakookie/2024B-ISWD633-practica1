# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](img/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor? 
Las imágenes y los contenedores en Docker se diferencian en que las imágenes son plantillas de solo lectura que contienen todas las bibliotecas, dependencias y configuraciones necesarias para crear un contenedor, mientras que los contenedores son instancias en ejecución basadas en esas imágenes. Las imágenes actúan como un esquema o instantánea del entorno de ejecución, mientras que los contenedores son los entornos aislados donde la aplicación se ejecuta, pudiendo ser modificados durante su uso. En resumen, las imágenes son el punto de partida y los contenedores son las implementaciones activas de esas plantillas.

![Imagen y contenedores](img/imagenContenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**
```
docker pull hello-world
```

**¿Qué es nginx**

Es un servidor web de código abierto que, desde su inicio en la gestión de servidores HTTP, ha evolucionado para ofrecer una amplia gama de funcionalidades. Actualmente, además de su función como servidor web, también se utiliza como proxy inverso, balanceador de carga HTTP, caché de contenido, y proxy de correo electrónico compatible con los protocolos IMAP, POP3 y SMTP. Gracias a su arquitectura eficiente, es popular para manejar grandes volúmenes de tráfico y optimizar el rendimiento de aplicaciones web.

Descargar la imagen  **nginx** en la versión **alpine**
```
docker pull nginx:alpine
```

### Listar imágenes

```
docker images
```
![docker](img/images.png)


# COLOCAR UNA CAPTURA DE PANTALLA DEL RESULTADO 

**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 
```
docker inspect hello-world
```

**¿Con qué algoritmo se está generando el ID de la imagen**
El ID de la imagen es un hash generado por el algoritmo SHA-256, que representa de forma única el contenido y configuración de la imagen en Docker.
![docker](img/algoritmoHash.png)

### Filtrar imágenes

```
docker images | grep <termino a buscar>

```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 
```
docker rmi hello-world
```
![docker](img/eliminarHelloWorld.png)

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```

