# Estandares abiertos en Cloud Native - Conceptos Clave para KCNA:
1. Open Container Iniciative [OCI] - Contenedores Estandarizados:
   * Que es Oci:
  		- La open Container Iniciative es una fundacion que define estandares abiertos para la creacion y ejecucion de contenedores, garantizando su portabilidad y compatibilidad en diferentes plataformas.
     - Objetivo del OCI:
       - Evitar la fragmentacion en el ecosistema de contenedores.
       - Asegurar que las imagenes y los runtimes de contenedores sean interoperables
       - Definir especificaciones estandar para contenedores.
     - Componentes Clave de OCI:
       - OCI Image Specification -> Define como se deben construir y almacenar las imagenes de contenedores
       - OCI Runtime Specification -> Establece como los Rnntimes [como runc o ContainerD] deben ejecutar los contenedores
       - OCI Distribution Specification -> Regula como las imagenes de contenedores deben ser distribuidas en registries.
	Ejemplo: Gracias a OCI, una imagen de contenedor creada en Docker puede ejecutarse en containerd o CRI-O sin problemas de compatibilidad.
2. Implementacion de referencia del Runtime de OCI:
   * OCI Proporciona una implementacion de ferencia para ejecutar contenedores siguiendo su estandar. La implementacion principal es runc, un runtime ligero para la ejecucion de contenedores que sigue la especificacion OCI
   * Principal Runtimes basados en OCI:
     * Runc -> Implementacion de referencia, usada por docker y Kubernetes.
     * containerd -> Runtine optimizado para Kubernetes, basado en runc.
     * CRU-O -> Runtime disenhado especificamente para Kubernetes.
		Ejemplo: Kubernetes no ejecuta con contenedores directamente, sino que usa containerd o CRI-O, ambos compatibles con OCI Runtime Specification
3. Tipos de Estandares Abiertos en Kubernetes:
	En Kubernetes, existen varios estandares abiertos que regulan la interaccion entre los distintos componentes del Cluster:

	Estandar					Significado					Proposito
	CNI							Container Network			Gestiona redes y contectividad entre pods
								Interface

	CRI							Container Runtine			Define como Kubernetes interacttua con runtimes de contenedores
								Interface

	CSI							Container Storage			Permite la integracion de soluciones de almacenamiento con Kubernetes
								Interface
* Explicaiones de cada estandar:
  * CNI [Container Network Interface]:
    * Regula la manera en que los contenedores se conectan a redes. Soluciones como Calico, Flannel y Cilium implementan CNI para manejar redes en Kubernetes
  * CRI [Container Runtime Interface]:
    * Permite que Kuernetes use diferentes runtimes de contenedores. Ejemplo: containerd y CRI-O implementan CRI para ejecutar contenedores en Kubernetes.
  * CSI [Container Storage Interface]:
    * Estandariza la integracion de sistemas de almacenamiento con Kubernetes. Proveedores como Amazon EBS, Google Persistent Disk y Ceph implementan CSI para ofrecer almacenamiento persistente a los pods.
Ejemplo Practico:
	* Kubernetes usa CRI para ejecutar contenedores con containerd o CRI-O
	* Usa CNI para conectar pods a la red con Calico o Flannel.
	* Usa CSI para manejar volumenes con AWS EBS o NFS
