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

[![ProjectDesign](https://www.herokucdn.com/deploy/button.png)](https://serene-bastion-37080.herokuapp.com/)

## Authors

* **Diego Gonzalez**


## License

This project is licensed under the GPL-3.0 license
