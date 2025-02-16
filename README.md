# CURSO DOCKER: SECCION 4 - DOCKER COMPOSE

## MULTI CONTAINER APPS

- Uso y conexión de volumen externo
- Bind volumes

Un volumen externo en Docker es un tipo de volumen que se almacena fuera del contenedor y que es gestionado por Docker, pero en lugar de estar directamente vinculado a un directorio específico en el sistema de archivos del host (como en los bind volumes), su ubicación es administrada por Docker. Los volúmenes externos se crean de forma que pueden ser reutilizados entre varios contenedores y no dependen de la estructura de directorios del host.

**Caracteristicas**
1. Gestión por Docker: Docker maneja la creación, almacenamiento, y ciclo de vida de los volúmenes. No necesitas preocuparte por la ubicación exacta del volumen en el sistema de archivos del host. Docker decide dónde almacenarlos.
2. Persistencia de datos: Los datos almacenados en un volumen externo persisten incluso si el contenedor que lo usa se detiene o elimina. Esto es útil para almacenar datos que no deben perderse cuando el contenedor se borra, como bases de datos.
3. Reutilización: Los volúmenes pueden ser fácilmente compartidos entre diferentes contenedores. Por ejemplo, varios contenedores pueden montar el mismo volumen para acceder a los mismos datos, lo cual es útil para mantener la consistencia de los datos entre servicios.
4. Independencia del host: A diferencia de los bind mounts, que dependen de un directorio específico del sistema de archivos del host, los volúmenes externos son agnósticos del sistema de archivos del host. Esto significa que el volumen puede ser utilizado por cualquier contenedor en cualquier sistema que ejecute Docker, lo que aumenta la portabilidad.

Un bind volume en Docker es una forma de compartir datos entre el sistema de archivos del contenedor y el sistema de archivos del host (tu máquina local o servidor). A través de un bind mount (o "bind volume"), puedes montar un directorio o archivo del host dentro de un contenedor, lo que permite que los datos persistan fuera del contenedor y que los cambios en esos archivos sean reflejados tanto dentro como fuera del contenedor.

**Caracteristicas**
1. Montaje de directorios/archivos específicos del host:
 - Un bind volume vincula un directorio o archivo específico del sistema de archivos del host a un contenedor, lo que significa que los archivos del contenedor pueden reflejarse directamente en el sistema de archivos del host.
 - A diferencia de los volúmenes gestionados por Docker, que son internos a Docker, los bind volumes están ligados a una ubicación exacta en el host.
1. **Acceso bidireccional:** Los cambios que se hagan en el archivo o directorio del host se reflejarán inmediatamente en el contenedor y viceversa. Es decir, puedes modificar los archivos directamente desde el host y esos cambios serán visibles dentro del contenedor, y si modificas los archivos desde el contenedor, los cambios se reflejarán en el host.
1. **Ideal para desarrollo:** Son muy útiles en entornos de desarrollo donde se necesita tener acceso directo a los archivos del contenedor desde el sistema de archivos del host. Por ejemplo, al trabajar con código fuente, puedes editar un archivo en tu editor local y ver los cambios reflejados al instante dentro del contenedor sin tener que reconstruirlo.
1. **No gestionado por Docker:** A diferencia de los volúmenes de Docker, los bind volumes no están gestionados por Docker. Tú eres responsable de la ubicación y el contenido del directorio o archivo en el host. Docker simplemente los monta en el contenedor.
1. **Dependencia del sistema de archivos del host:** Los bind mounts dependen de la estructura y ubicación del sistema de archivos del host. Si mueves el directorio o archivo en el host, el bind mount puede dejar de funcionar.
1. **Persistencia según el host:** La persistencia de los datos depende de la ubicación en el host. Si eliminas el directorio o archivo en el host, también se perderán los datos en el contenedor.
1. **Rendimiento:** Generalmente, los bind mounts tienen un mejor rendimiento que los volúmenes de Docker para algunos casos de uso, ya que los datos no necesitan ser gestionados por Docker y se accede directamente al sistema de archivos del host.
1. **Flexibilidad:** Puedes montar tanto archivos individuales como directorios completos, dándote flexibilidad sobre qué y cómo compartir los datos entre el contenedor y el host.

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