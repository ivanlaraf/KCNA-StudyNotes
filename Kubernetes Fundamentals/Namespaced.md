# Que es un Namespace en Kubernetes?
	 Un namespace en Kubernetes es como una "carpeta" dentro del cluster que ayuda a organizar y aislar recursos. Se usan cuando tienes varios equipos o proyectos ejecutandose en el mismo cluster.
# Ejemplo de la vida real:
* Piensa en una empresa con tres equipos:
	* Equipo Backend -> Necesita su propio espacio para ejecutar microservicios
	* Equipo Frontend -> Quiere aislar sus aplicaciones
	* Equipo QA -> Corre Pruebas sin afectar a los demas
[Cada_Equipo_puede_tener_su_propio_name_space_para_evitar_conflictos_entre_ellos]

# NameSpaces por defecto en Kubernetes:
	Cuando instalas Kubernetes, ya existen algunos namespaces:
		[kubectl get namespaces]
# Esto mostrara algo como:
	NAME              STATUS   AGE
	default           Active   1h
	kube-system       Active   1h
	kube-public       Active   1h
	kube-node-lease   Active   1h
# Explicacion Rapida:
	* Default -> Donde se crean los recursos si no especificas un namespace
	* kube-system -> Para los componentes internos de kubernetes
	* kube-public -> Contiene informacion accesible para todos
	* kube-node-lease -> Gestiona el estado de los nodos
# Ejemplo Practico:
	Crear un namespace llamado "dev":
		kubectl create namespace dev
	Crear un pod dentro de ese namespace
		kubectl run nginx --image=nginx --namespace=dev
	Ver los pods dentro del namespace "dev"
		kubectl get pods -n dev
	Eliminar un namespace [borra todos los recursos dentro de el]
		kubectl delete namespace dev

# Namespaced vs Non-Namespaced Kubernetes Components:
	Algunos recursos estan dentro de namespaces, otros son globales en el cluster.
	Ejemplo de recursos con namespace:
		* Pods
		* Deployments
		* Services
	Ejemplo de recursos sin namespace [globales en el cluster]
		* Nodes
		* PersistentVolumes
		* ClusterRoles
# Como saber si un recurso pertenece a un namespace:
	kubectl api-resources --namespaced=true
	kubectl api-resources --namespaced=false
# Namespaces y RBAC [Role Bases Access Control]
	Roles Bases Access Control [RBAC] y RoleBindings para definir que usuarios pueden hacer que cosas dentro de un namespace
# Ejemplo Practico:
	Crear un Role que solo permita pods en el namespace "dev"
	apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: dev
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
# Aplicarlo en Kubernetes
	kubectl apply -f role.yml
# Asignar este rol a un usuario con un RoleBinding
	apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: pod-reader-binding
  namespace: dev
subjects:
- kind: User
  name: juan  # Cambia esto por el usuario correcto
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
# Aplicarlo en Kubernetes:
	kubectl apply -f rolebinding.yml
# Ahora el usuario juan solo puede listar pods en el namespace "dev", pero no puede modificar nada mas.
