# Ejercicicio 1. Instalar chef en la máquina virtual que vayamos a usar.
Para instalar chef necesitamos ejecutar las siguientes líneas:

```
sudo apt-get install ruby1.9.1 ruby1.9.1-dev rubygems

sudo gem install ohai chef

curl -L https://www.opscode.com/chef/install.sh | bash
```

Y podemos ver que se ha instalado correctamente.
![ChequeoChefInstalado](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_038_zpssk9xlxig.png)

# Ejercicio 2. Crear una receta para instalar nginx, tu editor favorito y algún directorio y fichero que uses de forma habitual.
Para este ejercicio se va a instalar nginx y geany.

En la siguiente imagen vemos la estructura que deben de tener los ficheros de chef.
![ChefDirectorio](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_038_zps9n7ejpzw.png)

Dentro de cookbooks tenemos los distintas instalaciones que podemos hacer. Dentro de default.rb tenemos los paquetes que instalaremos al ejecutar ese cookbooks. En Geany instalamos geany, en nginx instalamos nginx y en CineForYou tenemos todos los paquetes encesarios para la api de cines.

Dentro de los archivos default.rb tenemos los paquetes que instalaremos.
![ChefPaquetes](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_039_zpskgdjopcg.png)

En la siguiente imagen podemos ver las configuraciones de node.json que es dónde se indica las recetas que se ejecutarán y en solo.rb indican dónde se encuentran los archivos de configuración.
![Chef archivos de configuración](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_040_zpsukaaxd3e.png)
# Ejercicio 3. Escribir en YAML la siguiente estructura de datos en JSON { uno: "dos", tres: [ 4, 5, "Seis", { siete: 8, nueve: [ 10, 11 ] } ] }

Para realizar este ejercicio he buscado información de wikipedia de JSON y YAML de los siguientes enlaces:
https://es.wikipedia.org/wiki/JSON

https://es.wikipedia.org/wiki/YAML

Y para comprobar que funciona correctamente he usado el siguiente convertidor de JSOn a YAML:
http://www.json2yaml.com/

En la siguiente imagen podemos ver la conversión correcta:
![JSONtoYAML](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_009_zpszh8k4pwj.png)


# Ejercicio 4. Provisionar una máquina virtual en algún entorno con los que trabajemos habitualmente usando Salt.

# Ejercicio 5. Desplegar los fuentes de la aplicación de DAI o cualquier otra aplicación que se encuentre en un servidor git público en la máquina virtual Azure (o una máquina virtual local) usando ansible.

Para solucionar el problema del openssl ese instalar los siguientes paquetes:
sudo apt-get install python-pip python-dev libffi-dev libssl-dev libxml2-dev libxslt1-dev libjpeg8-dev zlib1g-dev

Para configurar el ssh instalamos ssh-copy-id -p 2222 -i ~/.ssh/id_rsa.pub vagrant@localhost y comprobamos que funciona ahora sin pedirnos la contraseña.

Para realizar un ping para comprobar que lo hace bien con virtualbox utilizamos el siguiente comando:
ansible all -i 'localhost,' -c local -m ping





Actualizamos los repositorios
ansible ubuntu_local -m command -a "sudo apt-get update"

Instalamos github
ansible ubuntu_local -m command -a "sudo apt-get -y install git"
Con la opción -y le estamos indicando que

Ahora lo que hacemos es descargar la aplicación del repositorio.
ansible ubuntu_local -m git -a "repo=https://github.com/pmmre/Empresas.git dest=~/Calificaciones version=HEAD"

Ahora instalamos pip para poder instalar las dependecias del proyecto:
ansible ubuntu_local -m command -a "sudo apt-get -y install python-pip"

Como falta el paquete Error: pg_config executable not found.
instalamos lo siguiente:
ansible ubuntu_local -m command -a "sudo apt-get -y install libpq-dev python-dev"

Ahora instalamos todas las dependencias del proyecto
ansible ubuntu_local -m command -a "sudo pip install -r Calificaciones/requirements.txt"

Ahora instalamos nginx
ansible ubuntu_local -m command -a "sudo apt-get -y install nginx"

# Ejercicio 6. Desplegar la aplicación de DAI con todos los módulos necesarios usando un playbook de Ansible.


