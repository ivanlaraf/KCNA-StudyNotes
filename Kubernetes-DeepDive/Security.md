# Seguridad en Kubernetes:
# 1 Falco: Deteccion de amenazas en tiempo real
	Falco es una herramienta de deteccion de intrusiones en contenedores y Kubernetes.
	Monitorea eventos del sistema en tiempo real y detecta comportamiento sospechosos, como:
		* Intentos de ejectuar comandos dentro de un contenedor.
		* Accesos no autorizados a archivos sensibles.
		* Uso sospechoso de privilegios elevados.
	{Ejemplo}:
		Imagina que un atacante explota una vulnerabilidad en tu aplicacion y logra ejecutar bash dentro del contenedor. Falco lo detecta y envia una alerta antes de que cause mas danho.
	Comando Util:
		$ falco --list
	Muestra la lista de reglas de seguridad activas en falco
# 2. Open Policy Agent [OPA] - Politicas de seguridad para Kubernetes:
	OPA el Open Policy Agent es una herramienta que te permite definir politicas de control de acceso y validaciones para Kubernetes. Funciona con Gatekeeper, que impide que se desplieguen recursos que no cumplas con las reglas establecidas.
	Ejemplo:
		Si en tu empresa solo se permiten imagenes de un repositorio seguro, OPA puede bloquear despliegues con imagenes de Docker Hub
# 3. Kubescape - Escaneo de seguridad basado en estandares
	Kubescape analiza tu cluster de Kubernetes para asegurarse de que cumple con las mejores practicas de seguridad segun:
		* NSA [National Security Agency]
		* CISA
		* MITRE ATT&CK
	Ejemplo:
		Si ejecutas kubescape scan, la herramienta analiza tu cluster y te dice si:
		 * Tienes contenedores corriendo con privilegios de root
		 * Tus ConfigMaps contienen informacion sensible sin cifrar.
		Comando util:
			$ kubescape scan --submit
# 4. OpenID Connect [OIDC] - Autenticacion segura en Kubernetes:
	OIDC permite que los usuarios se autentiquen en Kubermnetes usando proveedores de identidad externos, como:
		* AWS IAM
		* Google
		* Microsoft
	[En lugar de usar credenciales estaticas en kubeconfig, puedes autenticarte con tu cuenta de Google y obtener permisos basados en roles]
# 5. Pod Security Policies [PSP] [Deprecado]:
	PSP ya no se usa, pero antes servian para restringir cosas como:
	* Evitar que los pods corran como root
	* Bloquear montajes de volumenes inseguros
	* Restringir el acceso a ciertos namespaces
	Su remplazo es Pod Security Admission [PSA] y OPA/Gatekeeper
# 6. LAS 4C's de la seguridad en Kubernetes
	Para proteger un cluster, hay que aplicar seguridad en 4 niveles:
	1. Cloud: Seguridad en la infraestructura donde corre Kubernetes [AWS, GCP, Azure]
	2. Cluster: Proteccion del Cluster [Autenticacion, control de acceso, Politicas]
	3. Container: Seguridad en la imagen del contenedor en si [No usar root por ejemplo]
	4. Codigo: Codigo seguro en las aplicaciones: [Evitar hardcoded secrets, validar entradas de usuario]
#
