# Challenge 1:Use the knowledge you've gained to create and run a container using the ubuntu container image. Run this as an interactive container, without the —rm option and with bash as the command Install a basic text editor like ‘nano’ or ‘vim’. Install htop and interact and use htop. You will need to make use of the apt package management tools to complete this task. Exit the container and clean up the exited container. Keep the container image.

	* docker pull ubuntu
	* docker run -it ubuntu bash
		- it permite el modo interactivo, escribir en la terminal del contenedor
		- ubuntu es la imagen
		- bash Indica que queremos iniciar con shell bash
		- apt install htop
		- apt install vim
		- htop
# Challenge 2:Repeat the first challenge but use the amazonlinux image which is based on CentOS to complete the same steps as in challenge 1, you will need to use different package management tools to succeed in this challenge. After completion, exit the container and clean up the exited container. Keep the container image.
	* docker pull amazonlinux
	* docker run -it amazonlinux bash
	* yum install vim
	* yum install nano
	* yum install htop
# Challenge 3: Run a ubuntu container that will automatically clean up after itself, we don’t need to use -it as we will only be running a single command. The command should be cat /etc/os-release
	- docker pull ubuntu:latest
	- docker run -it --rm ubuntu bash
	- cat /etc/so-release
# Challenge 4: Run an amazonlinux container that will automatically clean up after itself, we don’t need to use -it as we will only be running a single command. The command should be cat /etc/os-release
	-  docker run -it --rm amazonlinux bash
	- yum install ncurses
	- cat /etc/os-release
# Challenge 5: Remove the ubuntu container image using the traditional command line approach
	docker rmi amazonlinux
# Challenge 6: Remove the amazonlinux container image using the alternative command line approach
	docker rmi ubuntu
#
