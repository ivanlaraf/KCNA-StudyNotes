# Kubernetes Architecture
* [Kubelet]: Es un agente que corre en cada nodo del cluster
  * Se encarga de comunicarse con el CRI [Container Runtime Interface] para gestionar los contenedores
  * Asegura que los pods estan en ejecucion segun lo definido en el manifiesto de Kubernetes
	*Kubelet es como un supervisor dentro de cada nodo de Kubernetes. Su trabajo es asegurarse de que los Pods y contenedores esten funcionando correctamente en ese nodo*
	Imagina que es como un gerente de almacen que:
		- Recibe ordenes de Kubernetes API Server sobre que Pods deben estar en el nodo
		- Se agura que los Pods esten funcionando
		- Si un pod se pierde o se rompe, lo reporta y trata de reemplazarlo
* [Kube-Scheduler]:
  * Asigna los pds a los nodos del cluster la disponibilidad de recursos y restricciones definidas.
  * Se encarga de la distribucion eficiente de cargas en el cluster.
* [Kube-Proxy]:
  * Gestiona TODAS LAS REGLAS DE TED Y FACILITA la comunicacion entre los diferentes pods y servicios
  * Actua como un balanceador de carga interno en Kubernetes
* [kube-apiserver]:
  * Es el Punto de entrada principal de Kubernetes
  * Expone la API Rest de Kubernetes y gestiona todas las solicitudes del Cluster
  * Coordina la comunicacion entre los diferentes componentes
* [etcd]:
  * Es la base de datos clave-valor de Kubernetes donse se almacena el estado del cluster.
  * Es critico para la disponibilidad y consistencia del sistema.
* [Container_Runtimes]:
  * Alto nivel: Docker, containerd, cri-o [gestionan contenedores de manera abstracta]
  * Bajo nivel: runc [se encarga de la ejecucion real de los contenedores en el sistema]
*  [CCM_Cloud_Controller_Manager]:
   *  Permite la integracion de Kubernetes con servicios de la nube
   *  Se encarga de gestionar recursos como balanceador de carga, volumenes de almacenamiento etc.
   *  Se ejectua como un componentes independiente en el control plane del cluster.
#
