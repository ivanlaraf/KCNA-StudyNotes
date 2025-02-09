1. What is a Container Image?
   Container image es un paque portatil y autosuficiente de software que incluye todo lo necesario para ejecutar una aplicacion, como codigo, bibliotecas, configuraciones y dependencias.
   Esto permite que las aplicaciones se ejecutan de manera consistente en cualquier entorno, independientemente de las diferencias entre sistemas. Es fundamental para la portabilidad y la gestion de aplicaciones en arquitecturas nativas de la nube.
   Si queres seguir con mas preguntas o amplair sobre container images.
#
2. What's the difference between a container and a container image?
   A container is a running instance of the software, while a container image is a bundle of software [Un contenedor es una instancia en ejecucion del software, mientras que una imagen de contenedor es un paquete de software]
# Explicacion:
	* Container Image: Es un paquete estatico que contiene el software, las dependencias y las configuraciones necesarias para ejecutarlo. Es la plantilla de la cial se crean los contenedores.
	* Container [Contenedor]: Es una instancia activa y en ejecucion creada a partir de la imagen del contenedor. Puedes iniciarla, detenerla, eliminarla y ejecutarla en diferentes entornos.
3. que es un Container Registry?
	Un registro de contenedores es un repositorio centralizado donde se almacenan, gestionan y distribuyen imagenes de contenedores. Permite a los desarrolladores subir [push] imagenes al registro y descargarlas [pull] cuando sea necesario para ejecutar contenedores.
	# Puntos de Clave:
		1. Proposito
      		1. Almacenar imagenes de contenedores de forma estructurada y con control de versiones.
      		2. Facilitar la colaboracion y el uso compartido de imagenes entre equipos o entornos.
		2. Ejemplos
      		1. Registros Publicos: Docker Hub, Google Container Registrt, Amazon Elastic Container Registry [ECR]
      		2. Registrps privados: Registros autoalojados o repositorios privados administradpres en la nube, para almacenamiento seguro.
		3. Funcionalidad:
      		1. Push y pull: Los desarrolladores pueden subir imagenes desde su sistema local y descargarlas en otros entornos
      		2. Versionado: Las imagenes se etiquetan [Por ejemplo, App: v1.0, app:latest] para identificar facilmente las versiones.
		4. Control de acceso: Los registros suelen incluir permisos y politicas de seguridad para gestionar el acceso a las imagenes.
4. What is Latest?
   1. La etiqueta Latest en docker se utiliza como un alias para referirse a la versuin predeterminada de una iamgen de contenedor. Sin embargo, no significa que siempre sea la version mas reciente; [ simplemente es una etiqueta que los desarrolladores suelen usar para indicar una version especifica que desean que sea tratada como la predeterminada ]
# Proposito principal:
	* Conveniencia: permite a los usuarios ejecutar una imagen sin especificar una etiqueta exacta, por ejemplo, [docker pull nginx] es equivalente a docker pull nginx:latest
# Puntos clave:
	* No siempre es la mas reciente: La etiqueta "latest" puede ser un poco predecible, ya que no garanriza estabilidad si cambia la version asociada.
	* Buenas practicas, es mejor usar etiquetas especificas como v1.0, v1.1 en entornos de produccion para evitar inconsistencias.
# What is a digest in the context of container images?
Un digest es un identificador unico, algoa si como una huella digital, que se genera automaticamente para una imagen de contenedor. Este digest asegura que una imagen especifica no ha sido modificada y es exactamente la misma cada vez que la usas.