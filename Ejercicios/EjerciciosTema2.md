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

Dentro de cookbooks tenemos los distintas instalaciones que podemos hacer. Dentro de default.rb tenemos los paquetes que instalaremos al ejecutar ese cookbooks. En Geany instalamos geany, en nginx instalamos nginx y en CineForYou tenemos todos los paquetes necesarios para la api de cines.

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
```
sudo apt-get install python-pip python-dev libffi-dev libssl-dev libxml2-dev libxslt1-dev libjpeg8-dev zlib1g-dev
```

Una vez hecho esto instalamos instalamos ansibles.
```
sudo pip install paramiko PyYAML jinja2 httplib2 ansible
```

Ahora debemos de configurar ansible_hosts que es dónde configurar los grupos de servidores que es el nombre entre corchetes y dentro los servidores.
Para cada servidor pordemos configurar su s parámetros de entrada como la ip para acceder, el usuario al que se conectará y cuál es la llave pública.
![Configurar ansible_hosts](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_041_zpscyhmo2tu.png)

Los siguiente que tenemos que hacer es indicarle a ansible que utilcice estas direcciones: ```export ANSIBLE_HOSTS=~/ansible_hosts```

Y comprobamos que se puede realizar correctamente un ping a la máquina de AWS: ```ansible ubuntu -m ping```
![Ping a máquina AWS](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_042_zpsev5ls0wu.png)

Y ya podemos empezar a mandar ordenes remotamente a la máquina de ansible


Actualizamos los repositorios
```ansible ubuntu -m command -a "sudo apt-get update"```

Instalamos git y le indicamos con -y que instale las dependecias automáticamente.
```ansible ubuntu -m command -a "sudo apt-get -y install git"```


Ahora lo que hacemos es descargar la aplicación del repositorio.
ansible ubuntu -m git -a "repo=https://github.com/pmmre/Empresas.git dest=~/Calificaciones version=HEAD"
Y podemos ver en la siguiente imagen que descarga el repositorio. Si es amarillo indica que no estaba y lo esta completando, y si está verde indicaría que ya lo tiene.
![Imagen para descargar repositorio](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_043_zps1t2y7mvh.png)

Ahora instalamos pip para poder instalar las dependecias del proyecto:
```ansible ubuntu -m command -a "sudo apt-get -y install python-pip"```

Si tenemos el siguiente problema "Error: pg_config executable not found".
instalamos lo siguiente:
```ansible ubuntu -m command -a "sudo apt-get -y install libpq-dev python-dev"```

Ahora instalamos todas las dependencias del proyecto
ansible ubuntu -m command -a "sudo python Calificaciones/manage.py runserver 0.0.0.0:80"

Y ya podemos ver la web ejecutándose públicamente.
![Viendo web públicamente](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_044_zpsstbdsdto.png)


# Ejercicio 6. Desplegar la aplicación de DAI con todos los módulos necesarios usando un playbook de Ansible.

En este ejericio se configurará un archivo para instalar automáticamente todos los paquetes con ansible-playbook. En este caso se usarán los archivos de consiguración de ansibles y un script para ejecutarlo todo automáticamente.
En todos los casos los parámetros indican:
 - $1 indica que obtendremos como parámetro 1 la ip 
 - $2 indica que obtendremos como parámetro 2 el nombre de usuario de la máquina remota 
 - $3 indica que obtendremos como parámetro 3 la llave ruta de la llave pública

Un ejemplo de ejecución sería la siguiente línea:
![Ansible.sh parámetros](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_045_zpsxf5ylgjj.png) 

En el archivo ansible_hosts tenemos lo siguiente:
```
[ubuntu]
$1 ansible_ssh_user=$2 ansible_ssh_private_key_file=$3

```

Los paquetes que vamos a instalar los tenemos en el archivo calificaciones.yml:
```
- hosts: $1
  become: yes
  remote_user: $2
  tasks:
  - name: Actualizar sistema base
    apt: update_cache=yes upgrade=yes
  - name: Instalar paquetes
    apt: name=python-setuptools state=present
  - name: Instalar paquetes2
    apt: name=build-essential state=present
  - name: Instalar paquetes3
    apt: name=python-dev state=present
  - name: Instalar paquetes4
    apt: name=git state=present
  - name: Instalar pip
    action: apt pkg=python-pip
  - name: Obtener aplicacion con git
    git: repo=https://github.com/pmmre/Empresas.git dest=Empresas clone=yes force=yes
  - name: Permisos de ejecucion
    command: chmod -R +x Empresas
  - name: Instalamos dependencias
    command: sudo apt-get install -y libpq-dev python-dev
  - name: Instalamos los requirements
    command: sudo pip install -r Empresas/requirements.txt
  - name: ejecutar
    command: nohup sudo python Empresas/manage.py runserver 0.0.0.0:80
``` 

Y se usará el script ansible.sh para ejecutarlo todo:
```
#!/bin/bash
# ansible.sh

echo "La IP es: $1"
echo "Nombre de usuario: $2"
echo "Archivo .pem: $3"
cp ansible_hosts ansible_hosts2
cp calificaciones.yml calificaciones2.yml

sed -i 's/$1/'$1'/g' ansible_hosts2
sed -i 's/$1/'$1'/g' calificaciones2.yml

sed -i 's/$2/'$2'/g' ansible_hosts2
sed -i 's/$2/'$2'/g' calificaciones2.yml

sed -i 's/$3/'$3'/g' ansible_hosts2


export ANSIBLE_HOSTS=~/ansible_hosts

ansible-playbook calificaciones2.yml

rm ansible_hosts2 calificaciones2.yml
```

Una vez finalizado ya tendremos nuesta api ejecutandose en el servidor:
![Viendo web públicamente](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%202%20CC/Seleccioacuten_044_zpsstbdsdto.png)

