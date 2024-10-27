# Proyecto Flask con Docker Compose

Este proyecto es una aplicación web simple construida con Python y Flask, utilizando Docker y Docker Compose para la gestión de contenedores.

## Requisitos Previos

Asegúrate de tener instalados los siguientes programas en tu máquina:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/)

## Estructura del Proyecto

web-app/ 
├── docker-compose.yml 
├── database/ 
│ ├── Dockerfile 
│ └── init.sql
├── webapp/ 
│ ├── Dockerfile 
│ ├── requirements.txt 
│ └── app/ 
│ ├── init.py 
│ ├── app.py 
│ ├── config.py 
│ ├── models.py 
│ └── routes.py 
└── proxy/ 
├── Dockerfile 
└── nginx.conf


## Configuración de Docker Compose

El archivo `docker-compose.yml` define los servicios necesarios para ejecutar la aplicación, que incluye:

- **Webapp**: El servicio principal que ejecuta la aplicación Flask.
- **Base de datos**: El servicio que contiene la base de datos, si es necesario.
- **Proxy**: Un servicio opcional para manejar las solicitudes a través de un proxy inverso (ej. Nginx).

A continuación, se muestra un ejemplo básico del archivo `docker-compose.yml`:

```yaml
version: '3.8'

services:
  webapp:
    build:
      context: ./webapp
    ports:
      - "8080:8080"
    volumes:
      - ./webapp:/app

  database:
    build:
      context: ./database


  proxy:
    build:
      context: ./proxy
    ports:
      - "80:80"


Instrucciones de Uso
Clonar el Repositorio

Clona este repositorio en tu máquina local:

git clone <url_del_repositorio>
cd web-app

Construir y Ejecutar los Contenedores

Utiliza Docker Compose para construir y ejecutar todos los contenedores definidos en el archivo docker-compose.yml:

docker-compose up --build

Este comando construirá los contenedores según los archivos Dockerfile y ejecutará la aplicación Flask.

Acceder a la Aplicación

Una vez que los contenedores estén en funcionamiento, puedes acceder a la aplicación Flask en tu navegador web en http://localhost:8080.

Detener los Contenedores

Para detener y eliminar todos los contenedores, redes y volúmenes creados por up, ejecuta:

docker-compose down

Cómo Contribuir
Si deseas contribuir a este proyecto, siéntete libre de abrir un issue o un pull request. Tu ayuda es bienvenida.





