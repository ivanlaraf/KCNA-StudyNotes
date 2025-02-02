1 Serverless:
	El Patron [Serverless] es un modelo de computacion en la nube donde las aplicaciones se ejecutan sin necesidad de gestionar servidores de manera manual. Los recursos se asignan automaticamente segun la demanda y solo se paga por el tiempo de ejecucion.
#

* Caracteristicas Claves:
  * Escalabilidad automatica -> Se ajusta a la carga de trabajo sin intervencion manual
  * Pago por Uso -> Solo se paga cuando el codigo se ejecuta.
  * Menos Gestion de Infraestructura -> No es necesario administrar servidores o configuraciones complejas.
  * Desarrollo Agil -> Permite a los desarrolladores centrarse en el codigo y no en la infraestructura.
*
# Ejemplos:
	* Aws Lambda: Ejecuta funciones sin necesidad de administrar servidores.
	* Google Cloud Functions: Procesa eventos como mensajes en una cola o cambios en una base de datos.
#

# Porque adoptar Serverless en Cloud Native?
	* Reduce costos operativos
	* Facilita la integracion con Microservicios y Eventos
	* Aumenta la velocidad de Desarrollo y despliegue
#

2. CloudEvens y su importancia en Cloud Native
	Los CloudEvents son un estandar para describir eventor en entornos Cloud Native, Facilitando la interoperabilidad entre diferentes servicios y plataformas.
	#Ejemplo de un CloudEvent en JSON:
		{
  			"specversion": "1.0",
  			"type": "com.example.object.created",
  			"source": "/storage-bucket",
  			"id": "1234-5678-91011",
  			"time": "2025-02-01T12:34:56Z",
  			"datacontenttype": "application/json",
  			"data": {
    			"objectId": "file123.jpg",
    			"size": "4MB"
  			}
		}
# Porque son importantes?
	* Estandarizacion -> Permiten que aplicaciones y servicios se comuniquen de manera uniforme
	* Interoperabilidad -> Facilitan la integracion entre plataformas como Kubernetes, Knative, AWS y Google Cloud
	* Mejora la Observabilidad -> Ayudan a rastrear eventos y automatizar respuestas en tiempo real.
	* Ejemplos de Uso:
    	* Un servicio en Knative recibe un CloudEvent cuando se sube un archivo a un bucket de almacenamiento y ejecuta un proceso automatico
  	*
#
