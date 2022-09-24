# AREP-TALLER-CLIENTE-SERVER

El siguiente repositorio se crea con el fin de afianzar conocimiento acerca de los servidores web y como hacer contacto con el cliente mediante métodos distintos a Spark y Spring.


### Prerequisites

- Maven - Administrador de dependencias y administrador del ciclo de vida del proyecto
- Java - Ambiente de desarrollo
- Git - Sistema de control de versiones
- Heroku - Plataforma de despliegue

### Installing

Para descargar el proyecto y compilarlo de manera local puede clonar el repositorio con el siguiente comando:

    git clone https://github.com/DiegoGonzalez2807/AREP-CLIENT_SERVICE_EXERCISES.git


Ejecutar el programa mediante consola con el siguiente comando. También genera el ciclo de vida de este.

    mvn clean package exec:java -D "exec.mainClass"="edu.escuelaing.arem.httpServer.HttpServer"


## Running the tests

Para ejecutar las pruebas unitarias se ejecutan con el siguiente comando:

    mvn test

## Documentation

Para crear la documentación del proyecto se hace con el siguiente comando:

    mvn javadoc:javadoc

## Deploying in Heroku

## Primer Reto
Escriba un servidor web que soporte múlltiples solicitudes seguidas (no concurrentes). El servidor debe retornar todos los archivos solicitados, incluyendo páginas html e imágenes. Construya un sitio web con javascript para probar su servidor. Despliegue su solución en Heroku. NO use frameworks web como Spark o Spring, use solo Java y las librerías para manejo de la red.

### Solución reto 1
Para este reto se crean dos componentes principales: 
    
- Servidor Web: Encargado de abrir la conexión entre el cliente y el servidor, así como de escuchar las peticiones
- Writer: Se encarga de mostar el recurso que requiere el usuario

### Funcionalidad del Writer
1. El writer va a revisar el path Y el clientSocket que le manda el servidor.
2. Se tienen arreglos que contienen las extensiones que soporta el aplicativo para traerlas al usuario
```java
//Lista de extensiones de texto
    static List<String> Extension_text = new ArrayList<String>(
            Arrays.asList(".html",".js",".css")
    );
    //Lista de extensiones de imagenes
    static List<String> Extension_Image = new ArrayList<String>(
            Arrays.asList(".png",".jpg")
    );
```
3. Se tiene una clase principal llamada "writer", la cuál revisa la extensión del path dado por el servidor. Si la extensión corresponde a tipo texto, se manda a leer el archivo. Si es una extensión de tipo imágen, se manda a escribir la imágen. Se hace un mapeo de los arreglos mediante funciones lambda "Stream".
```java
        if(Extension_text.stream().anyMatch(extension -> file.contains(extension))){
            extensionFile = file.split("\\.")[1];
            System.out.println("EXTENSION "+extensionFile);
            writeText();
        }
        else if(Extension_Image.stream().anyMatch(extension -> file.contains(extension))){
            extensionFile=file.split("\\.")[1];
            writeImage();
        }
```

### Cliente Web
Para este apartado, se usa las funciones de writer antes mencionadas. En este caso se hace un archivo index.html en la carpetas "resources/public". La idea es que apenas empiece a ejecutar el servidor web, este revise si el usuario pone como contexto http://localhost:4567 (Esto para ejectuar el servidor de manera local). Esta petición manda al writer una petición con un path /index.html, el cuál se lo va a mostrar.
Esta página está conectada a un cliente JS llamado app.js

El cliente JS se encarga de mandar la solicitud de traer mediante una URI específica, el recurso

```java
        if(path.equals("/")){
        path = "/index.html";
        }
        ServerWriter.writer(path,clientSocket);
```

```javascript
        function traerPerrito(){
    window.location.href = "http://localhost:4567/prueba.png";
}

function traerHTML(){
    window.location.href = "http://localhost:4567/pruebaIndex.html";
}
```

![](https://github.com/DiegoGonzalez2807/AREP-CLIENT_SERVICE_EXERCISES/blob/master/resources/images/PruebaInicio.png)


### Pruebas 
#### Prueba de Imagen
![](https://github.com/DiegoGonzalez2807/AREP-CLIENT_SERVICE_EXERCISES/blob/master/resources/images/pruebaImagen.png)

#### Prueba de texto
![](https://github.com/DiegoGonzalez2807/AREP-CLIENT_SERVICE_EXERCISES/blob/master/resources/images/pruebaHTML.png)


#### Implementación Heroku
[![ProjectDesign](https://www.herokucdn.com/deploy/button.png)](https://salty-fjord-82376.herokuapp.com/)

## Authors

* **Diego Gonzalez**


## License

This project is licensed under the GPL-3.0 license
