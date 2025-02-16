# CURSO DOCKER: SECCION 4 - DOCKER COMPOSE

## ¿Para que sirve docker-compose.yml?

**Docker Compose** es una herramienta que permite definir y administrar aplicaciones multi-contenedor de Docker. Usualmente, se usa para configurar y ejecutar aplicaciones que requieren varios servicios, como bases de datos, servidores web, sistemas de cache, etc., todo en un entorno aislado y reproducible.

En lugar de tener que:
- Buscar las imagenes y descargarlas manualmente desde consola
- Crear contenedores que usen dichas imagenes
- Crear una red si varios de esos contenedores se comunican entre si, ej: Este repositorio tiene una base de datos **postgresql** y un gestor **pgAdmin** que trabajan en conjunto

**Basicamente te permite definir múltiples contenedores:** Usando un archivo *docker-compose.yml* donde se especifican todos los contenedores necesarios para tu aplicación, como bases de datos, servicios backend, frontend, etc.

**Configuración simplificada:** En este archivo, puedes definir las redes, volúmenes, puertos y variables de entorno necesarias para cada servicio, lo que hace que sea mucho más fácil gestionar configuraciones complejas

**Arranque y detención de servicios con un solo comando:** Al usar el comando ```docker-compose up```, todos los contenedores necesarios para la aplicación se inician automáticamente, y con docker-compose down, los puedes detener y eliminar.

**Escalabilidad:** Puedes usar Docker Compose para escalar ciertos servicios en tu aplicación, iniciando varios contenedores de un mismo servicio con un solo comando.

*En resumen, Docker Compose facilita la administración de entornos complejos al permitirte definirlos de manera declarativa y gestionarlos con comandos simples.*