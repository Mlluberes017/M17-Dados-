# M17 - Actividades DevOps - Simulador de Dados

Este repositorio contiene el desarrollo de las actividades del modulo M17 relacionadas con Git, Docker y Jenkins.

La aplicacion consiste en un simulador de lanzamiento de dados desarrollado en Python. El programa utiliza la librer√≠a `dice` para realizar los lanzamientos y muestra los resultados en pantalla con una pausa de 5 segundos entre cada lanzamiento.

## Actividad 1 - Git

En esta actividad se trabajo≥ con control de versiones utilizando Git y GitHub.

Se realizaron las siguientes acciones:

- Creacion de un repositorio publico en GitHub.
- Primer commit con el archivo `README.md`.
- Segundo commit con el codigo de la aplicacion.
- Tercer commit modificando el mensaje de salida.
- Revert del √ultimo commit.
- Creacion de la rama `feature/rol`.
- Modificacion del dado a 20 caras en la rama `feature/rol`.
- Modificacion de la cantidad de lanzamientos a 6 en la rama `main`.
- Merge de los cambios de `main` hacia `feature/rol`.

## Actividad 2 - Docker

En esta actividad se creo≥ una imagen Docker para ejecutar la aplicacion.

Se agrego≥ un archivo `Dockerfile` utilizando Python 3.10 como imagen base. La imagen instala las dependencias necesarias desde `requirements.txt` y ejecuta el archivo `main.py`.

La imagen fue subida a DockerHub:

https://hub.docker.com/r/mlluberes/m17-dados

## Actividad 3 - Jenkins

En esta actividad se creo un pipeline de integracion y despliegue continuo utilizando Jenkins.

El pipeline se define en el archivo `Jenkinsfile` y realiza las siguientes etapas:

- Limpieza del workspace.
- Clonado del repositorio desde GitHub.
- Construccion de la imagen Docker.
- Ejecucion del contenedor de prueba.
- Eliminacion del contenedor creado.
- Subida de la imagen a DockerHub.

El pipeline finalizo≥ correctamente y la imagen fue publicada en DockerHub.

## Archivos principales

- `README.md`: documentacion del proyecto.
- `main.py`: c√≥digo principal de la aplicacion.
- `requirements.txt`: dependencias del proyecto.
- `Dockerfile`: definicion de la imagen Docker.
- `Jenkinsfile`: definicion del pipeline de Jenkins.

## Ejecucion local

Para ejecutar la aplicacion localmente:

```bash
pip install -r requirements.txt
python3 main.py
