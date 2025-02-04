# Gobernanza y Comunidad de CNCF - Conceptos Claves para KCNA
	En la CNCF, la comunidad y la gobernanza juegan un papel esencial en el desarrollo y mantenimiento de tecnologias Cloud Native. Para el examen KCNA, es crucial comprender como se gestionan los conflictos, el significado de siglas comnes y el rol del Technical Oversight Commitee [TOC]
1. Resolucion de Conflictos en CNCF
   1. Los proyectos de CNCF involucran multiples grupos de trabajo con colaboradores de todo el mundo, lo que puede generar conflictos en la toma de de decisiones.
   *Como se manejan los conflictos*
      - Codigo de conducta -> Todos los miembros deben seguir las reglas de respeto y colaboracion.
      - Proceso de mediacion -> Se establecen procedimientos para resolver desacuerdos de manera transparente.
      - Gobernanza basada en consenco -> Se fomenta la toma de decisiones colectivas en lugar de imponen soluciones unilaterales.
      - Apelacion y escalamiento -> Si un conflicto no se resuelve en un grupo, se puede escalar al TOC o CNCF Governing Board
EJEMPLO: Si hay un desacuerdo sobre una nueva funcionalidad en Kubernetes, el tema se discute en la comunidad, se abre un issue en GitHub y, si es necesario, se eleva el TOC
2. Acronimos Comunes en CNCF:
Lista de Siglas que debes conocer para KCNA:
*Acronimo*					*Significado*
	CNCF						Cloud Native Computing Foundation
	TOC							Technical Oversight Commitee
	SIG							Special Interest Group
	TAG							Technical Advisory Group
	OCI							Open Container Initiative
	K8s							Kubernetes
	CI/CD						Continuos Integration / Continuos Delivery
	OPA							Open Policy Agent
	Etcd						Distributed Key-Value Store usado en Kubernetes
3. ROL del CNCF Technical Oversight Committe [TOC]
   1. Que es el TOC: el TOC es el organismo de CNCF responsable de supervisar y guiar la direccion tencica de los proyectos Cloud Native
   2. Responsabilidades del TOC:
      1. Revision y aprobacion de nuevos proyectos -> Evaluan si un proyecto cumple con los principios Cloud Native antes de aceptarlo en CNCF.
      2. Sueprvision del estado de los proyectos -> Definen si un proyecto es  Sandbox, Incubating o Graduated
      3. Definicion de mejores practicas -> Promueven estandares para mejroar la interoperabilidad y seguridad
      4. Coordinacion con SIGs u TAGs -> se comunican con los Special Interest Groups [SIGs] y los Technical Advisory Groups [TAGs] para avanzar en tecnologias clave.
*EJEMPLO: K8s paso por todas las etapas en CNCF antes de convertirse en un proyecto Graduado, gracias a la supervision del TOC*
