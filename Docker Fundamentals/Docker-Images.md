# Container Images:
	Definicion: Una container Image es un paquete ligero y autonomo que contiene todo lo encesario para ejecutar una aplicacion: el codigo, las dependencias, las bibliotecas y el sistema operativo necesario en su version minima
# Importancia:
	Aseguran consistencia: lo que funciona en un entorno local funcionara igual en produccion
	Simplifican el despliegue de aplicaciones al empaquetar todo en un solo archivo.
	Ejemplo: una Imagen de Docker podria contene runa aplicacion Python junto con su runtime, dependencias y configuracion, como Python 3.9
# Contenedores vs Imagenes:
	1. Imagenes:
      	1. Son Estaticas. es el archivo base o plantilla que contiene la aplicacion y sus dependencias.
      	2. No estan "Vivas"; no ejecutan procesos.
      	3. Pueden ser almacenadas en repositorios llamados registries
		* Ejemplo: Docker Registry *
	2. Contenedores:
      	1. Son dinamicos: Se crean a partir de imagenes y ejecutan procesos en un entorno aislado
      	2. Un contenedor es una instancia en ejecucion de una imagen.
      	3. Ejemplo Practico: Si tienes una imagen de Node.JS, al "correr" esa imagen, tendras un contenedor ejecutando tu aplicacion node.
	#
#

# Container Registries:
	* Definicion: Un container registry es un repositorio donde se almacena imagenes de contenedores
	* Tipos:
    	* Registries Publicos: Como Docker Hub, Amazon ECR Public, o Github Container Registry.
    	* Registries Privados: empresas pueden alojar sus propias imagenes en registries privados para mayor seguridad.
	* Funcion: Facilitan la distribucion de imagenes, permitiendo descargarlas y utilizarlas en cualquier entorno.
	* Ejemplo: docker pull ubuntu:20.04 descarga la iamgen ubuntu: 20.04 desde Docker Hub
# Container Image Tags
	* Definicion: Un tasg es una etiqueta asignada a una version especifica de una imagen.
	* Ejemplo: Una Imagen puede tener multiples etiquetas como Python: 3.9 y python: latest
	* Aqui, 3.9 indica una version especifica, mientras que latest apunta a la version mas reciente.
# El proposito del tag latest
	Que significa?
		el Tag latest se usa para indicar la version predeterminada o mas reciente de una imagen.
		Ejemplo: Al ejecutar docker pull nginx, se descarga nginx:latest si no especificas una etiqueta/tag
# Cuidado con latest"
	No siempre es la mejor opcion, porque puede cambiar sin previo aviso.
	En produccion, es mejor especificar una version fija, como nginx: 1.21.6, para evitar problemas de compatibilidad.
#
