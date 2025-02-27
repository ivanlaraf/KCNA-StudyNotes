# Kubernetes tiene un Scheduler que decide en que nodo Se ejecuta un pod [Su principal funcion]
# Ejemplo:
	Imagina que Kubernetes es una empresa de repartos y los Pods son paquetes.
		* Hay varios repartidores [Nodos] en diferentes zonas.
		* El Scheduler decide que repartidor [Nodo] entrega cada paquete [Pod] Segun reglas y disponibilidad.
		[Pero si queremos elegir un repartidor especifico, usamos Nodename o nodeSelector]
# Que es nodeName?
	noName forza un pod a ejecutarse en un nodo especifico
		* Es como decirle a Kubernetes. "Este pod solo puede correr en este servidor especifico".
		* Si el nodo esta caido, el Pod nunca arrancara.
			apiVersion: v1
			kind: Pod
			metadata:
  				name: mi-pod
			spec:
  				nodeName: nodo-1  # 👈 Este Pod solo correrá en "nodo-1"
  				containers:
                - name: nginx
    				image: nginx
	- Pros: Sencillo y directo
	- Contras: No hay tolerancia a fallos, si nodo-1 se apaga, el Pod no podra ejecutarse en otro lado
# Que es nodeSelector?
	Permite elegir un grupo de nodos con ciertas caracteristicas
	* Usa labels para seleccionar nodos
	* Mas flexible que nodeName, si un nodo falla, Kubernetes puede elegir otro con la misma etiqueta.
				apiVersion: v1
				kind: Pod
				metadata:
  					name: mi-pod
				spec:
  				  nodeSelector:
    				tipo: alto-rendimiento  # 👈 Kubernetes buscará un nodo con esta etiqueta
                  containers:
                    - name: nginx
                      image: nginx
# Diferencias Claves nodeName vs NodeSelector:
	* Nodename es flexible? = NO
	* Tolerante a Fallos? = NO
	* NodeSelector Permite elegir nodos con una etiqueta especifica, es flexible? = SI
	* NodeSelector, permite elegir nodos con una etiqueta especifica, es tolerante a fallos? = SI
# Resumen:
	* Kubernetes Scheduler asigna los pods a los nodos automaticamente.
	* nodeName: fuerza a un pod en correr en nodo especifico [sin tolerancia a fallos].
	* nodeSelector: Selecciona nodos por etiquetas [mas flexibles].
# Ejercicios:
	* nodeName:
		# desplegamos con nodeName forzamos desplegarlo
