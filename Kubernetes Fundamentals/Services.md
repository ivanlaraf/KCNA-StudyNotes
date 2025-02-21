# Que son los Services en Kubernetes?
	Un Service en Kubernetes es un objeto que expone un conjunto de Pods a traves de una direccion IP estable, lo que permite la comunicacion dentro del cluster.
# Ejemplo Real:
	Tiene varios pods corriendo una app, pero sus IPs cambian constantemente. Service crea un punto de acceso fijo para que otros servicios o usuarios pueden comunicarse con ellos
# Tipos de objetos o services en Kubernetes
Existen 4 tipos principales de Services en Kubernetes
* Cluster IP [DEFAULT]: Expone el servicio dentro del cluster, no accesible desde afuera.
* NodePort: Expone el servicio en un puerto especifico de cada nodo del cluster
* LoadBalancer: Expone el servicio a internet con un balanceador de carga externo
* Headless Service: No asigna una IP Fija, en su lugar devuele las IPS de los pods
