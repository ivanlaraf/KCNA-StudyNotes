# Cloud Native Fundamentals Spanish Version #

Las replicaciones nativas en la nube aprovechan el poder del Entorno Cloud para mejorar aspectos fundamentales como:

- Resiliencia
- Agilidad
- Operabilidad
- Observabilidad

Examinemos cada una de estas:

# Resiliencia

- Una aplicacion resiliente esta preparada para resistir fallos y seguir funcionando, en todo caso recuperarse facilmente. Para lograrlo, utilizan patrones como:
  - Redundancia: Duplicar componentes criticos para evitar puntos unicos de falla
  - Failover: Cambio automatico a una instancia de respaldo en caso de fallo
  - Degradacion Controlada: Mantener una funcionalidad minima cuando ocurre una falla

  # EJEMPLO

        Un ejemplo clave de resiliencia en entornos cloud-native es la auto-recuperacion. En Kubernetes por ejemplo, si un pod falla, el sistema automaticamente lo reemplaza para mantener la cantidad deseada de replicas.

  #

#

# Agilidad

    La agilidad en aplicaciones nativas en la nube se refiere a la capacidad de desarrollar, modificar y desplegar tu software rapidamente. Para lograrlo, se aplican practicas como:

    * Microservicios: Arquitectura que permite desarrollar y actualizar componentes individuales sin afectar toda la aplicacion

    * Entrega Continua [CI/CD]: Automatizar el ciclo de vida del software, facilitando despliegues frecuentes y confiables

    La automatizacion juega un papel clave en la agilidad, ya que permite responder rapidamente a cambios del mercado o nuevas necesidades del usuario

#

# Operabilidad

    La operabilidad se centra en la facilidad de implementacion, ejecucion y administracion de aplicaciones. Para garantizar una buena operabilidad, las aplicaciones nativas en la nube:
    * Son faciles de monitorear y configurar:
    * Utilizan herramientas de IaC como Terraform, para gestionar entornos de manera reproducible y automatizada
    * Minimiza el trabajo manual [toil], reduciendo errores humanos y mejorando la eficiencia operativa

#

# Observabilidad

    La observabilidad permite comprender el estado interno de un sistema a partir de los datos que genera. Es clave para diagnosticar problemas y analizar el comportamiento de la aplicacion en produccion.
  * Se basa en los tres pilares de la observabilidad:
	- Logging: Registro de eventos importantes para analisis de problemas
	- Monitoring: Supervision de metricas para detectar anomalias
	- Tracing: Rastreo de solicitudes a traves de multiples servicios para diagnosticar latencias y errores
#

# Memorizar con la regla "RAOO"
	Para recordar estas caracteristicas de manera sencilla, puedes usar la regla "RAOO", que significa:
	- Resiliencia
	- Agilidad
	- Operabilidad
	- Observanilidad
#

Los mapaches son a menudo observadores: Racoon Are Often Observant

