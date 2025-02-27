# Kubernetes NetworkPolicies:
	Las NetworkPolicies en Kubernetes sirven para controlar quien puede comunicarse con quien dentro del cluster. Por defecto, todos los Pods pueden hablar entre si, pero con NetworkPolicies, puedes reestringir el trafico entre ellos.
# Ejemplo:
	Piensa en una oficina donde todos pueden hablar con todos. Pero un dia, el jefe decide que los empleados del departamento de Finanzas pueden hablar con recursos humanos y no con otros departamentos. Eso es exactamente lo que hace una NetworkPolicy en Kubernetes.
# Ejemplo basico de un NetworkPolicy:
	Tienes un Pod con la etiqueta app: backend y quieres que solo reciba trafico desde Pods con la etiqueta app:frontend.
			apiVersion: networking.k8s.io/v1
			kind: NetworkPolicy
			metadata:
  				name: allow-frontend-to-backend
			spec:
 			 podSelector:
   			  matchLabels:
    		   app: backend  # Aplica esta política a los pods con esta etiqueta
 			 policyTypes:
				- Ingress  # Estamos controlando el tráfico entrante
 			ingress:
             - from:
              - podSelector:
                matchLabels:
                 app: frontend  # Solo los pods con esta etiqueta pueden comunicarse
# Aplica la politica de NetworkPolicy:
	kubectl apply -f network-policy.yaml
# Verifica que se creo correctamente:
	kubectl get networkpolicy
# Elimina la politica si es necesario:
	kubectl delete networkpolicy allow-frontend-to-backend
# Puntos clave para el examen KCNA:
	* Las NetworkPolicies son acumulativas -> Si aplicas varias, se suman en lugar de reemplazarse.
	* Solo funcionan si hay un CNI compatible como Calico o Cilium
	* Pueden restringir trafico de entrada [Ingress] y salida [Egress]
# CNI [Container_Network_Interface]:
	el Container Network Interface es el sistema que gestiona la red dentro del cluster de Kubernetes
# Eejemplo de CNI:
	Piensa en CNI como los cables invisibles que conectan todos los Pods dentro de Kubernetes incluso si estan en nodos diferentes. Sin el CNI, los pods no podrian comunicarse
# Algunos CNI populares:
	* Flannel [sencillo y facil de usar]
	* Calico [Seguridad avanzada y control de trafico]
	* Cilium [usa eBPF para mejorar el rendimiento]
# Que hace el CNI en la practica?
	* Le asigna una IP
	* Le conecta con la red del cluster
	* Se encarga de que pueda comunicarse con otros Pods
# Sin un CNI, los Pods estarian aislados y no podrian hablar entre ellos.
