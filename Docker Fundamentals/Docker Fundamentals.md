Antes de Kubernetes, es importante entender algunos conceptos basicos de los contenedores. En esta seccion, hay dos terminos clave que pueden aparacer en el examen KCNA
Namespaces -> Separan y aislan procesos dentro del sistema
Cgroups [Control Gorups] -> Controlan el uso de recursos como CPU y memoria

1. Que son los Namespaces?
   1. Los namespaces permiten que diferentes procvesos dentro del mismo sistema operativo se ejecuten de manera aislada, sin interferir entre si.
   Ejemplo Facil: Imagina que tienes dos aplicaciones corriendo en el mismo servidor. Cada uno debe tener sus propios archivos, red y procesos sin mezclarse con la otra. Los namespaces crean esa separacion.
	*Tipos de Namespaces mas importantes*:
	- PID Namespace -> Aisla los procesos, evita que un proceso de un contenedor vea los procesos de otro.
	- NET Namespace -> Da a cada contenedor su propia configuracion de red.
	- MNT Namespace -> Aisla el sistema de archivos para que cada contenedor tenga su propio entorno
	Ejemplo real: Cada contenedor en Docker usa Namespaces para asegurarse de que sus procesos y redes sean independientes.
2. Que son los Cgroups [Control Groups]:
   1. Para que sirven?
      1. Los Control Groups controlan cuantos recursos puede usar un proceso.
		Ejemplo Facil: Piensa en una computadora compartida: si un usuario usa toda la memorioa y CPU, los demas se quedan sin recursos. Cgroups evitan esto limitando cuanto puede usar cada proceso.
		# que recursos controlan los cgroups:
			 * CPU -> puede decirle a un contenedor que solo use el 50% del procesador
			 * Memoria -> Puedes limitar la RAM que un contenedor puede consumir
			 * Red y almacenamiento -> Controla cuanto trafico o espacio en disco puede usar un contenedor
*	*	#

# Que es chroot?
	Permite cambiar el entorno del sistema al directorio que desee, aislando los procesos que se ejecuten alli por ejemplo.
	sudo chroot /mnt/sistema-nuevo
	Docker no usa directamente chroot, pero emplea un concepto mas avanzado y seguro basado en el: namespaces y cgroups
	Por que no usa chroot directamente?
		chroot solo cambia el directorio raiz del proceso, pero no aisla otros recursos como red o la memoria
		Docker necesita un aislamiento mas fuerte.
# Como se llama originalmente Docker:
	Docker originalmente se llamaba dotCloud.
	*Historia*:
		* Fue creado por Solomon Hykes en 2010 como parte de una plataforma PaaS [Platform as a Service] llamada dotCloud
		* en 2013, la empresa decidio abrir su tecnologia de contenedores como un proyecto independiente y lo llamo Docker.
   * Dato Interensante:
     * Dot Cloud no tuvo tanto exito como plataforma, pero la tecnologia de contenedores detras si, por lo que la empresa cambio su enfoque completamente a Docker
     * en 2014, dotCloud fue vendida y la empresa paso a llamarse Docker Inc.
Resumen rapido:
   * Nombre Original: dotCloud
   * Anho del cambio: 2013
   * Motivo: La tecnologia de contenedores tuvo mas exito que la plataforma PaaS original.
# Cuales son los dos ingredientes clave que Docker combino para crear su solucion?
	Docker unio dos tecnologias principales:
	1. Namespaces -> Aislamiento de procesos y recursos
	2. Cgroups [Control Groups] -> Control y limitacion de recursos
# Namespaces -> Aislamiento total:
	Docker usa namespaces de Linux para que cada contenedor tenga su propio:
	* Espacio de procesos independiente.
	* Red separada.
	* Sistema de archivos propio
	Un contenedor no puede ver ni interactuar con procesos fuera de su espacio.
# Cgroups -> Control de recursos:
	Docker usa Cgroups para definir cuanta CPU, RAM, o red puede usar un contenedor
	Ejemplo:
		Puedes limitar un contenedor a solo 512MB de RAM y 1 CPU:
			docker run --memory="512m" --cpus="1" my-container
# Cuantos namespaces fueron agregados originalmente al kernel de Linux en 2002?
en 2002 se agregaron 6 namespaces al kernel de Linux:
1. Mount: Para aislar el sistema de archivos
2. PID: Para aislar los identificadores de procesos
3. IPC: para aislar la comunicacion entre procesos
4. Network: Para aislar interfaces y configuraciones de red.
5. User: Para aislar IDs de usuario y privilegios
6. UTS: Para aislar nombres de host y dominio
Docker establece la base para tecnologias como Docker, que aprovechan estos namespaces para garantizar wel aislamiento de los contenedores
