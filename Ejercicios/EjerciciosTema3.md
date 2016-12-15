# Gestión de infraestructuras virtuales

## Ejercicio 1. Instalar una máquina virtual Debian usando Vagrant y conectar con ella.
Para realizar este ejercicio lo primero es añadir el box de debian de la página oficial usando el siguiente comando `vagrant box add debian {url}`.
![vagrant box](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%203%20CC/Ejercicio%201/Seleccioacuten_012_zpsen410su4.png)

Despues de realizar esto ejecutar `vagrant init debian`.
![vagrant init](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%203%20CC/Ejercicio%201/Seleccioacuten_013_zpsujci3ght.png)

Una vez creado el archivo Vagranfile ahora podemos crear una máquina, o inicializar si ya esta creada, con `vagrant up`.
![vagrant up](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%203%20CC/Ejercicio%201/Seleccioacuten_068_zpseggmdvzi.png)

Y podemos ver  que podemos acceder a ella por ssh, usando `vagrant ssh`.
![vagrant ssh](http://i393.photobucket.com/albums/pp14/pmmre/CC/Ejercicios%20Tema%203%20CC/Ejercicio%201/Seleccioacuten_069_zpsm8id1iez.png)

## Ejercicio 2. Instalar una máquina virtual ArchLinux o FreeBSD para KVM, otro hipervisor libre, usando Vagrant y conectar con ella. 



## Ejercicio 3. Crear un script para provisionar `nginx` o cualquier otro servidor web que pueda ser útil para alguna otra práctica

## Ejercicio 3. Configurar tu máquina virtual usando `vagrant` con el provisionador ansible



# Automatización de tareas en la nube

## Ejercicio 1. Crear una máquina virtual Ubuntu e instalar en ella un servidor nginx para poder acceder mediante web.

## Ejercicio 2. Crear una instancia de una máquina virtual Debian y provisionarla usando alguna de las aplicaciones vistas en el tema sobre herramientas de aprovisionamiento


## Ejercicio 3. Conseguir una cuenta de prueba en OpenStack y crear una instancia a la que se pueda acceder, provisionándola con algún script disponible.
