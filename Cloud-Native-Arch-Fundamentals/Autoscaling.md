1. Escalado Horizontal vs Escalado Vertical

	El escalado en la nube es una estrategia clave para ajustar los recursos y garantizar un rendimiento optimo segun la demanda. Existen dos enfoques principales:
# Escalado Horizontal [Scaling Out/In]:
	Consiste en agregar o eliminar instancias de una aplicacion para manejar la carga de trabajo.
	* Permite distribuir la carga entre multiples instancias
	* Mejora la tolerancia a fallos y la dispinibilidad
	* Es el enfoque mas utilizado en entornos Cloud Native
	Ejemplo: En Kubernetes, El Hotizontal Pod Autoscaler [HPA] incrementa o reduce el numero de pods segun el uso de CPU o metricas personalizadas
# Escalado Vertical [Scaling Up/Down]:
	Consiste en aumentar o reducir RECURSOS de una instancia unica e individual [mas CPU, mas RAM, etc.]
	* Es util cuando escalar horizontalmente no es viable
	* Puede generar downtime si se requiere reiniciar la aplicacion
	* Menos flexible en comparacion con el escalado horizontal
	Ejemplo: En Kubernetes, el VPA [Vertical Pod Autoscaler], ajusta dinamicamente los recursos asignados a un pod en funcion de su consumo real

2. Kubernetes Cluster Autoscaler:
   El Cluster Autoscaler es una herramienta clave en Kubernetes que permite ajustar automaticamente el numero de nodos en un clister en funcion de la demanda de recursos
	# Funcionamiento:
		1. Scale up: Cuando no hay suficientes nodos para programar nuevos pods, se agregan nodos al cluster.
		2. Scale Down: Cuando un nodo tiene pocos pods en ejecucion, Kubernetes puede eliminarlo para optimizar costos.
		Ejemplo: En un cluster, en AWS EKS, el Cluster Autoscaler puede aumentar automaticamente el numero de nodos EC2 cuando hay mas demanda y reducirlo cuando la carga disminuye
	#
3. KEDA y el concepto de Scaling to Zero:
   KEDA [Kubernetes Event-Driven Autoscaling] es una herramienta avanzada que permite escalar aplicaciones en funcion de eventos en tiempo real, como la llegada de mensajes a una cola o el consumo de una API
	* Conceptos clave:
    	* ScaledObjects: Son recursos que definen como KEFA escala un despliegue segun metricas extener
    	* Scaling to Zero: KEDA permite reducir el numero de replicas a cero, cuando la carga de trabajo es nula, lo que ahorra costos en entornor serverless
    	* Ejemplo: Lambda en AWS puede ejecutarse solo cuando recibe una solicitud, en lugar de mantener un servidor activo todo el tiempo. Con KEDA, Kubernetes puede replicar este comportamiento, iniciando pods solo cuando son necesarios.
4. Diferencias entre VPA Y HPA:

# Característica		HPA (Horizontal Pod Autoscaler)							VPA (Vertical Pod Autoscaler)
Tipo de escalado		Agrega o elimina pods.									Ajusta CPU/RAM de los pods existentes.
Basado en métricas		CPU, RAM o métricas personalizadas.						Consumo real de recursos del pod.
Flexibilidad			Alta, recomendado para microservicios.					Menos flexible, útil para cargas predecibles.
Tiempo de reacción		Rápido, ajusta la cantidad de pods dinámicamente.		Más lento, requiere reiniciar pods en algunos casos.
Ejemplo de uso			API que recibe muchas solicitudes concurrentes.			Base de datos en un contenedor con una carga variable.

HPA -> es ideal par amanejar picos de trafico de manera dinamica.
VPA -> Es util cuando se necesita ajustar el rendimiento sin cambiar la cantidad de pods.
