# Challenge 1: Pull the latest version of the alpine image using the traditional docker command format

docker pull alpine---> or maybe we can go something like docker pull alpine:latest

# Challenge 2: Compare the digest in the pull command output to that on Docker Hub. You may be surprised to see that they don’t actually match!

The reason being, in the video when we used the funbox image which is an image with a single architecture only. The alpine image covers many different variants such as amd64 and arm and hence, the digest shown in the ‘docker pull’ output is a top level digest that references all platform variants that you see individually listed in the Docker Hub output.

There’s a convenient tool that you can use that will show the top level digest, compare the top of this report to what you see in the docker pull output - https://explore.ggcr.dev/?image=alpine


# Challenge 3: Use the docker history command to inspect the layers that comprise of this image
	Los layers en docker son capaz que se aplican para crear la Imagen "Image". Cada vez que creas una imagen docker, esta se contruye sobre capas previas. Cada capa contiene una serie de cambios o instrucciones realizadas sobre la capa anterior. Estas capas son reutilizables y permiten que Docker sea mas eficiente al construir y ejecutar contenedores.
	Ejemplo Sencillo:
		Imagina que estas construyendo una [caja] [la imagen de docker] que contiene varios elementos. Cada elemento que agregas es una capa
		1. La primera capa la vamos a llamar base, tienes una caja vacia por ejemplo una imagen basae como al[one o ubuntu. esa es nuestra base principal.]
		2. Segunda capa: Luego, pones dentro de la caja un libro [por ej le instalas Pyrhon 3.9] esta es una nueva capa que agrega algo a la caja.
		3. Tercera capa: Despues, agregas una lampara [comienzas a modificar un archivo de configuracion]. Esa es otra capa
	Por que es util?
		* Reutilizacion: Si otra imagen usa la misma base o la misma capa de Python, Docker no tiene que volver a descargarla o recrearla, la usa directamente
		* Eficiencia: Si solo cambias una capa, no necesitas reconstruir toda la imagen, solo se actualiza la capa que cambio.

# Challenge 4: Compare this to the layers listing on Docker Hub
	From Docker Hub:
		FROM scratch
		ADD alpine-minirootfs-3.21.2-x86_64.tar.gz /
		CMD ["/bin/sh"]

		[From scratch] : Esto significa que la imagen empieza desde cero [sin una base preexistente]. Scratch es un punto de partida vacio para construir una imagen personalizada.

		ADD alpine-minirootfs-3.21.2-x86_64.tar.gz /:
			Esta linea agrega el archivo comprimido alpine-minirootfs-3.21.2-x86_64.tar.gz al contenedor, que contiene el sistema de archivos raiz de Alpine. Este archivo es basicamente una version muy ligera de linuz, con solo lo esencial apra que Alpine funcione
		CMD ["/bin/sh"]
			Define el comando que se ejecutara por defecto cuando inicies un contenedor basado en esta imagen. En este caso, esta configurado para ejecutar el shell /bin/bash
# Challenge 5: Identify the image id and digest
		 56fa17d2a7e7 and digest id: con docker images --digests sha256:56fa17d2a7e7f168a043a2712e63aed1f8543aeafdcee47c58dcffe38ed51099
# Challenge 6: Remove the alpine image and confirm that it is removed
 con docker rmi, [remove image] podemos borrarlo luego vemos con docker images
# Challenge 7: Capture a specific version of ubuntu by using the tag 20.04 and the alternative command syntax in the format of docker noun verb
 docker pull ubuntu:20.04
# Challenge 8: Check the digest, using the alternative command syntax
	docker images --digests
# Challenge 9: Inspect the layers of this image using docker history, via the alternative command syntax
	docker history ubuntu:20.04
# Challenge 10: Remove the ubuntu:20.04 image using the alternative command syntax and confirm that it is removed, again using the alternative command syntax
 docker rmi  ubuntu:20.04
