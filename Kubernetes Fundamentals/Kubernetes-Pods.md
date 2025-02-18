# Que es un pod?
	* Es la unidad mas chica de Kubernetes.
	* Contiene uno o mas contenedores que comparten almacenamiento y red.
	* Se ejecutan en un nodo dentro del cluster.
# Ejemplo de la vida real:
[Aplicacion_Streamlit_Kubernetes]:
	- En lugar de ejecutar tu app en un contenedor suelto, creas un Pod que contiene el contenedor con tu app de Streamlit
	- Kubernetes se encarga de que ese Pod se mantenga en ejecucion
[Crear_Pods_CLI_y_YAML]
# Metodo imperativo:
	Ejecuta un pod directamente con un comando:
	*Kubectl run mi-app --image=streamlit/hello*
	ESTO CREA UN POD con el Contenedor streamlit/hello
# Metodo Declarativo [YAML]:
	Usamos una rchivo YAML para definirlo y aplicarlo con kubectl apply -f archivo.yaml
	[Ejemplo]:
		apiVersion: v1
		kind: Pod
		metadata:
			name: mi-app
		spec:
			containers:
				- name: streamlit
				  image: streamlit/hello
	[Ejecutarlo]:
		kubectl apply -f mi-app.yaml
# Diferencia:
	- CLI [Imperativo]: rapido pero menos reutilizable
	- YAML [Declarativo]: mas organizado y escalable
# Acceder a la documentacion de un pod:
	Si necesitas ayuda con los campos de un Pod, usa:
	*kubectl explain pod.spec*
	Ejemplo:
		kubectl explain pod.spec.containers
	* Esto te muestra la documentacion de los contenedores dentro de un Pod
# Ejecutar un comando en un Pod en ejecucion:
	si tu Pod ya esta corriendo y quieres entrar a el:
	kubectl exec -it mi-app -- /bin
	[Si estas usando ubuntu como imagen, podrias usar bash:]
	kubectl exec -it mi-app --bash
# Ejemplo:
	Entras al contenedor de tu app de Streamlit y pruebas comandos como ls, pwd, etc.

[Politicas_De_Reinicio_de_un_Pod]:
	Cuando un pod falla, Kubernetes puede reiniciarlo segun la politica que tenga:
	* Always [por defecto] -> siempre se reinicia si falla
	* OnFailure -> Solo se reinicia si termina con error.
	* Never -> No se reinicia nunca
Ejemplo en YAML:
	spec:
		restartPolicy: OnFailure
	UseCases:
		Si tu app de STreamlit falla, Kubernetes puede reiniciarla automaticamente si usas Always.
# Red con los Pods: Comunicacion sin NAT
	Cada por tiene su propia IP, pero los contenedores dentro de un mismo Pod comparten la misma red
	* Ejemplo de la vida real:
    	* Imagina un pod con tu app de Streamlit y otro contenedor que coge logs
    	* Ambos contenedores pueden comunicarse facilmente por que estan dentro del mismo Pod y comparten IP
  	* Para quen un Pod hable con otro Pod en el cliuster, se usa el nombre del Pod o un service:
		{curl http://mi-otro-pod:5000}
# Sidecars e Init Containers:
	Son tecnicas para ejecutar contenedores auxiliares dentro de un Pod.
# Sidecar: complementa el contenedor principal:
	Ejemplo de la vida real:
		* Tienes un Pod con tu app de Streamlit
		* Agregar un Sidecar que guarda logs en otro contenedor
		spec:
			containers:
				- name: streamlit
					image: streamlit/hello
				- name: logger
					image: busybox
					command ["sh", "-c", "tail -f /var/log/app.log"]
	Casos de uso:
		Tu aplicacion escribe logs y otro contenedor [Sidecar] los analiza y envia a un servidor externo
# Init container:
	Un init container es un contenedor especial en un Pod que se ejecuta antes de los contenedores principales y se detienen cuando termina su tarea.
	Su proposito es preparar el entorno antes de que la aplicacion principal inicie.
#

# Problema de los comandos Imperativos:
	Los cambios no quedan guardados en un archivo YAML, lo que puede llevar a configuracion inconsistente.
	Por eso, en enornos de produccion, se recomienda usar el metodo declarativo con archivos YAML, asegurando que toda la configuracion queda documentada y versionada en Git.
# Ejemplo con metodo declarativo:
	apiVersion: v1
	kind: Pod
	metadata:
		name: my-nginx
	spec:
		containers:
		- name: nginx
		  image: nginx
[Luego_Aplicas_el_archivo_con]
*kubectl apply -f my-nginx.yaml*

Los comandos imperativos le dicen a Kubernetes que hacer de inmediato, sin necesidad de archivos de configuracion
Ejemplo: kubectl run my-nginx --image=nginx
