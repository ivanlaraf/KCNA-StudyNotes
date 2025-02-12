# Challenge: Create and run 3 Nginx containers with different content using volumes. Each container should serve its own custom HTML page. Each container should be accessible on the localhost with it’s own unique port.
	- mkdir website 1
	- mkdir website 2
	- mkdir website 3

	- echo "<h1> Welcome to Server 1</h1> > /website_1/index.html
  	- echo "<h1> Welcome to Server 2</h1> > /website_2/index.html
	- echo "<h1> Welcome to Server 3</h1> > /website_3/index.html
  *Hora de comenzar ejecutando los contenedores*

	docker run -d -p 8081:80 -v ~/website_1:/usr/sjare/nginx/html --name  nginx1 nginx
	docker run -d -p 8082:80 -v ~/website_2:/usr/share/nginx/html --name  nginx2 nginx
	docker run -d -p 8083:80 -v ~/website_#:/usr/share/nginx/html --name nginx3 nginx
  [Explicando_conceptos]
	-d -> Modo detached para ejecutar en segundo plano
	-p 808X:80 -p mapea el puerto 808X en tu maquina al 80 del contenedor
	-v ~/website_X:/isr/share/nginx/html -> Usa la carpeta con HTML personalizado
	--name nnginxX -> asigna un nombre al contenedor
	nginx -? usa la imagen oficial de Nginx
