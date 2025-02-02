# Pilares Claves de la Arquitectura Cloud Native
	Ademas de las caracteristicas fundamentales de las aplicaciones nativas en la nube, la arquitectura Cloud Native, se basa en cuatro pilares esenciales, que permiten construir sistemas agiles, resilientes y escalables
#

1. Arquitectura de Microservicios:
   La arquitectura de Microservicios consiste en dividir una aplicacion en componentes pequenhos, independientes y especializados en una sola funcion
   # Beneficios:
     * Agilidad -> Permite desarrollar y desplegar servicios por separado sin afectar toda la aplicacion.
     * Escalabilidad -> Cada microservicio puede escalarse de forma independiente segun la demanda.
     * Resiliencia -> Un fallo en un servicio no afecta NECESARIAMENTE A TODA LA APLICACION
     * Ejemplo: Netflix utiliza microservicios para manejar distintas funciones como la reproduccion de video, las recomendaciones y la autenticacion de usuarios de manera separada.
	#
2. Contenerizacion:
   1. La contenerizacion encapsula una aplicacion con todas sus dependencias dentro de un contenedor, garantizando que funcione de manera consistente en cualquier entorno.
   2. Beneficios:
      1. Aislamiento -> Los contenedores son independientes entre si, evitando conflictos de dependencias.
      2. Consistencia -> Una aplicacion funciona igual en entornos de desarrollo, prueba y produccion
      3. Eficiencia -> Los contenedores consumen menos recursos que las maquinas virtuales tradicionales.
		Ejemplo: Docker permite ejecutar la misma aplicacion en una laptop de desarrollo y en un Cluster de Kubernetes sin cambios
3. DevOps
   DevOps es una cultura y conjunto de practicas que integran Desarrollo [Dev] y Operaciones de TI [Ops] para mejorar la eficiencia y calidad del software
	* Principios clave:
    	* Automatizacion -> Reduce errores y acelera despliegues
    	* Monitoreo continuo -> Detecta y corrige problema rapidamente
    	* Colaboracion -> Facilita la comunicacion entre equipos de desarrollo y operaciones
		Ejemplo: Empresas como Amazon y Google aplican DevOps para realizar multiples despliegues diarios sin interrumpir sus servicios
4. Entrega Continua [CD- Continuos Delivery]:
   1. Le entrega continua [CD] permite que los cambios en el codigo se construyan, prueben y preparen automaticamente para su despliegue en produccion
   * Beneficios:
     * Ciclos de lanzamiento mas rapidos -> Las  nuevas funcionalidades llegan antes a los usuarios.
     * Mayor productividad -> Menos tiempo dedicado a tareas manuales
     * Reduccion de riesgos -> Se minimizan errores en el despliegue
		Ejemplo: Github Actions y AWS CodePipeline permiten que cada cambio en el codigo pase por pruebas automaticas antes de ser desplegado
	*
# Mnemotecnica:
	Para recordar estos cuatro pilares, usa la regla:
	Morning Coffe Delivers Caffeine Delight
	[Microservices, Containerisation, DevOps, Continuos Delivery]
	- Microservicios -> Modularidad, escalabilidad, resiliencia.
	- Contenerizacion -> Portabilidad, aislamiento, eficiencia.
	- DevOps -> Automatizacion, monitoreo, colaboracion.
	- Entrega Continua -> Despliegues rapidos, seguros y eficientes
#
