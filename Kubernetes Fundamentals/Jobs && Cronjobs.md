# Jobs y CronJobs en Kubernetes:
Cual es la diferencia entre Job y CronJob:
	* Un Job es un proceso que corre una vez y termina
	* Un CronJob es como un cron en Linux: se ejecuta en intervalos programados
# Ejemplo basico:
	1. Crear un Job en Kubernetes
		Un job que imprime "Hola Mundo" y termina:
				apiVersion: batch/v1
				kind: Job
				metadata:
					name: mi-job
				spec:
				 template:
				   spec:
					containers:
					- name: hola
					  image: busybox
					   command: ["echo", "Hola Mundo desde Kubernetes"]
					restartPolicy: Never
# Creamos el Job con Kubectl:
	kubectl apply -f job.yaml
# ver Jobs activos:
	kubectl get jobs
# Ver logs del Job:
	kubectl logs job/mi-job
# Eliminar el job:
	kubectl delete job mi-job
#

# Crear un Cronjob en Kubernetes:
* Ejemplo: Un CronJob que ejecuta un comando cada minuto
		apiVersion: batch/v1
		kind: CronJob
		metadata:
  			name: mi-cronjob
		spec:
  			schedule: "*/1 * * * *"  # Se ejecuta cada minuto
  			jobTemplate:
    		spec:
      			template:
        			spec:
          				containers:
                        - name: mi-cron
            			image: busybox
            			command: ["echo", "Este mensaje se repite cada minuto"]
          				restartPolicy: Never
# Crear el CronJob con kubectl
	kubectl apply -f cronjob.yaml
# Listar Cronjobs:
	kubectl get cronjobs
# Ver los Jobs que ha generado con CronJob:
	kubectl get jobs
# Ver logs de un CronJob:
	kubectl logs job/mi-cronjob
# Eliminar un CronJob
	kubectl delete cronjob mi-cronjob
#

 Ejercicio práctico que podemos hacer ahora
1️⃣ Crea un Job en Kubernetes que imprima "Hola Kubernetes".
2️⃣ Ejecuta un CronJob cada 5 minutos que imprima "Esto es un cronjob en Kubernetes".
3️⃣ Lista y observa los Jobs y CronJobs en ejecución.
4️⃣ Elimina los recursos creados al terminar
