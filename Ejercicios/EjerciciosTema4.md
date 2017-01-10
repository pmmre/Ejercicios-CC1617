# Virtualización ligera usando contenedores

## Ejercicio 1. Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en GitHub como en el sitio web está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 2.0.

Para instalar lxc debemos de ejercutar el siguiente comando : `sudo apt install lxd-client`

Una vez estalado comprobamos la versión que tenemos instalada de lxc con `lxc --version`, como podemos observar en la siguiente imagen:

![versión_LXC](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Seleccioacuten_001_zpsujxhsqtc.png)

Para comprobar que lxc funciona correctamente ejecutamos el comando `lxc-checkconfig` y en la siguiente imagen podemos comprobar que en nuestro caso funciona correctamente.

![lxc_funcionando](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Seleccioacuten_002_zpswehlddjy.png)





## Ejercicio 2. Instalar una distro tal como Alpine y conectarse a ella usando el nombre de usuario y clave que indicará en su creación

Para crear alpine debemos de ejecutar el siguiente comando `sudo lxc-create -t <distribución_que_queremos_instalar> -n <nombre_del_contenedor>`, en nuestro caso será `sudo lxc-create -t alpine -n alpine`.

![Instalación_alpine](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%202/Seleccioacuten_003_zpsnaacfrbl.png)

Para inicializar un contenedor debemos de ejercutar `sudo lxc-start -n <nombre_del_conteneder`, que en nuestro caso es alpine. Y podemos comprobar que contenderes tenemos y en que estado están con `sudo lxc-ls -f`.

![Estado_de_los_contenedores](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%202/Seleccioacuten_004_zpsycs8mpxy.png)

Y por ultimo podemos iniciar sesión en el contenedor utilizando `sudo lxc-console -n <nombre_del_contenedor>` (-n alpine).


![Inicio_de_sesión_en_alpine](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%202/Seleccioacuten_005_zps9ysfcpio.png)

Resultan interesantea los siguientes comandos:
 - `sudo  lxc-destroy -n <nombre_del_contenedor>` para poder eliminar contenedores que no deseemos.
 - `sudo lxc-stop -n <nombre_del_contenedor>` para detener un contenedor.


## Ejercicio 3. Provisionar un contenedor LXC usando Ansible o alguna otra herramienta de configuración que ya se haya usado.

Lo primero que debemos de hacer es instalar el plugin de vagrant para lxc: `vagrant plugin install vagrant-lxc`

![instaldo_el_plugin_vagrant-lxc]()

## Ejercicio 4. Instalar una imagen alternativa de Ubuntu y alguna adicional, por ejemplo de CentOS.
Lo primero que debemos de hacer es instalar docker con el siguiente comando: `sudo apt-get install docker.io`
Y ahora ejecutamos el servicio de docker: `sudo service docker start`

Ahora instalamos ubuntu usando: `sudo docker pull ubuntu`

![Instalando_ubuntu](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%204/Seleccioacuten_005_zpsqwq0ibm8.png) 

Ahora instalamos centOS usando: `sudo docker pull centos`

![Instalando_centos](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%204/Seleccioacuten_006_zpsvjkazo46.png)

Y podemos ver los contendedores instalados en el sistema usando: `sudo docker images`

![Contenedores_instalados](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%204/Seleccioacuten_007_zpshegvab2w.png)


## Ejercicio 5. Crear a partir del contenedor anterior una imagen persistente con commit.

En este ejercicio crearos un commit de un estado del sistema.

Ejecutamos el comando `sudo docker ps -a` para ver los ultimos estados de los sistemas. Ahora realizamos un commit ejecutando `sudo docker commit <ID> <nombre_commit>` y podemos ver el nuevo commit en `sudo docker images`.

![Creación_del_commit](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%205/Seleccioacuten_012_zps31aw8n3n.png)

Podemos construir montar el contenedor del commit con `sudo docker build -t pablo/commit-ubuntu .`

![montar_commit](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%205/Seleccioacuten_014_zpsfj1ppm00.png)

Y podemos realizar un ssh con `sudo docker run -it pablo/commit-ubuntu sh`

![ssh_en_commit](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Ejercicio%205/Seleccioacuten_015_zpsvmhjhuwe.png)



