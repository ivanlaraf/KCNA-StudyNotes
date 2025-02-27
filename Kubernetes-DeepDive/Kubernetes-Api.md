# LA API de Kubernetes:
	La API de Kubernetes es el corazon del cluster. Es el sistema que recibe peticiones [como crear pods, cambiar configuraciones o consultar el estado de recursos] y las procesa
# Ejemplo de la vida real:
	Imagina que Kubernetes es un restaurante y la API Server es el mesero:
		* Tu como cliente haces un pedido como crear un pod
		* El Mesero, es decir la API toma la orden y la valida
		* Envia la orden a la cocina [Scheduler y Kubelet] Para que preparen la comida [crear el pod]
		* Finalmente, te entregan la comida [el pod esta listo]
# 1. CRD [CUSTOM Resource Definitions] - Extender la API:
	Un CRD permite a los usuarios crear nuevos tipos de recursos en Kubernetes
	Ejemplo: Si Kubernetes no tiene un recurso para manejar "Bases de datos", podemos crear un CRD, llamado Datababase para gestionar bases de datos como si fueran Pods o Deployments.
		apiVersion: apiextensions.k8s.io/v1
		kind: CustomResourceDefinition
	metadata:
  		name: databases.miempresa.com
	spec:
  		group: miempresa.com
  		names:
    		kind: Database
    		plural: databases
  		scope: Namespaced
  		versions:
        - name: v1
    		served: true
    		storage: true
# Authorization-mode - Seguridad en la API:
	Kubernetes controla quien puede hacer que con --authorization-mode
* Modo comunes:
  * RBAC: Role-Based Access Control -> Define permisos por usuario/rol
  * Webhook -> Usa servicios externos para decidir permisos
  * AlwaysAllow -> No recomendado permite todo sin restricciones
# Ejemplo de como ver el modo actual:
	kubectl get pod -n kube-system -l component=kube-apiserver -o yaml | grep authorization-mode
#

# Los 3 pasos que sigue una peticion en la API:
	Cuando envias un comando kubectl o un app llama a la API, sigue este flujo:
1. Autentication:
   1. Kubernetes verifica quien eres [ejemplo: usando certificados o tokens]
2. Autorizacion: Kubernetes revisa si tienes permiso para hacer esa accion [RBAC]
3. Admision: Kubernetes usa reglas para extra para validad la solicitud antes de ejecutarla [ejemplo: evitar que un pod use demasiada memoria]

Ejemplo Practico:
	Si intentas eliminar un pod sin permisos:
		kubectl delete pod mi-pod
	Kubernetes rechazara la peticion en la etapa de autorizacion
