# Virtualización ligera usando contenedores

## Ejercicio 1. Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en GitHub como en el sitio web está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 2.0.

Para instalar lxc debemos de ejercutar el siguiente comando : `sudo apt install lxd-client`

Una vez estalado comprobamos la versión que tenemos instalada de lxc con lxc `--version`, como podemos observar en la siguiente imagen:

![versión_LXC](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Seleccioacuten_001_zpsujxhsqtc.png)

Para comprobar que lxc funciona correctamente ejecutamos el comando `lxc-checkconfig` y en la siguiente imagen podemos comprobar que en nuestro caso funciona correctamente.

![lxc_funcionando](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%204%20CC/Seleccioacuten_002_zpswehlddjy.png)


