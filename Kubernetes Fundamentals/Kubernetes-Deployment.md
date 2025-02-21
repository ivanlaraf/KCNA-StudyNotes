# Kubernetes Deployments y ReplicaSets:
[Relacion Entre Deployments y ReplicaSets]:
	* ReplicaSet: Se encarga de asegurarse de que haya una cantidad especifica de replicas de un pod corriendo en todo momento.
	* Deployment: Es un nivel superior que gestiona los ReplicaSets y permita actualizar pods sin downtime
# Ejemplo Practico:
	Cuando vas a crear un Deployment, Kubernetes automaticamente crea un ReplicaSet y este ReplicaSet se encarga de mantener el numero desea de pods corriendo, es decir muere un pod se replica y crea otro.
	apiVersion: apps/v1
	kind: Deployment
metadata:
  name: mi-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: mi-app
  template:
    metadata:
      labels:
        app: mi-app
    spec:
      containers:
      - name: mi-app
        image: nginx
# En este caso:
	- Un deployment ha creado un ReplicaSet
	- El Replica Set se encarga de mantener 3 pods corriendo con la imagen de Nginx
# Estrategias de Deployment en Kubernetes:
	- RollingUpdate [Viene por defecto]: Actualiza los pods poco a poco, sin downtime
		strategy:
  type: RollingUpdate
  rollingUpdate:
    maxSurge: 1
    maxUnavailable: 1
*Si tienes una app con 3 pods corriendo y actualizas la imagen, Kubernetes remplaza los pods uno por uno para evitar interrupciones*
	- Recreate:
		Elimina todos los pods y luego los vuelve a crear con la nueva version [causa downtime]
		strategy:
			type: Recreate
		Util cuando una app no puede tener multiples versiones corriendo al mismo tiempo [por ejemplo, bases de datos en memoria]
# como monitorear un deployments:
[VER_ESTADO_DE_UN_DEPLOYMENT]:
EL CLASICO:
	kubectl get deployments
	Muestra cuantos pods estan listos y cuantos deberian estarlo
# Ver un progreso de un rollout
	kubectl rollout status deployment mi-app
Te indica si hay algun problema en el despliegue

# VerReplicaSets creados por un deployment:
	kubectl get rs
	rs =replicasets
# Monitorear el progreso de un Deployment
	Para asegurarte de que el despliegue se realizo correctamente, puedes hacer esto:
# Veriificar los logs de un Deployment:
	Para asegurarte de que el despliegue se realizo correctamente, puedes hacer esto:
# Verificar logs de los pods:
	kubectl logs -f deployment/mi-app
# Ver eventos del Deployment:
	kubectl describe deployment mi-app
# Hacer Rollback si algo sale mal:
	kubectl rollout undo deployment mi-app
# Esto revierte el despliegue a la version anterior en caso de errores

 Ejercicio práctico en tu laboratorio
1️⃣ Crea un Deployment con 3 réplicas de un contenedor Nginx.
2️⃣ Actualiza el Deployment con una nueva imagen de Nginx.
3️⃣ Monitorea el estado del rollout.
4️⃣ Realiza un rollback a la versión anterior.
