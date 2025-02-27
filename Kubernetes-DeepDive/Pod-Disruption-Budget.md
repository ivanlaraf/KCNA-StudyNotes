# PDB [Pod_Disruption_Budget]:
	* Un Pod Disruption Budget [PDB] es una politica que define cuantos Pods pueden ser interrumpidos al mismo tiempo en un Deployment, StatefulSet o ReplicaSet.
# Para que sirve?:
	* Evitar downtime en aplicaciones criticas
	* Proteger replicas minimas para que la app siga funcionando
	* Controlar las actualizaciones sin afectar la disponibilidad del servicio.
# Ejemplo sencillo:
	Imagina que tienes 3 Pods corriendo una app de Streamlit y aplicas un PDB con minAvailable: 2.
	Si intentas actualizar todos los Pods a la vez, Kubernetes solo permitira interrumpir 1 pod porque al menos 2 deben estar activos.
# Ejemplo de YAML de un PDB:
		apiVersion: policy/v1
        kind: PodDisruptionBudget
        metadata:
         name: my-app-pdb
        spec:
         minAvailable: 2  # Al menos 2 Pods deben estar activos
         selector:
          matchLabels:
           app: my-app
{Este PDB asegura que minimo 2 pods sigan acticos cuando haya una interrupcion}
