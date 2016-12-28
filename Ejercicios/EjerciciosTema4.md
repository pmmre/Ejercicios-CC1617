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

