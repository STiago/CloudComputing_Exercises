#Ejercicios semana 9 - Orquestación de máquinas virtuales

##Ejercicio 1
####Instalar una máquina virtual Debian usando Vagrant y conectar con ella.

En primer lugar descargamos la máquina virtual de Debian usando vagrant con el siguiente comando:

`vagrant box add debian-jessie https://atlas.hashicorp.com/ARTACK/boxes/debian-jessie`

Seguidamente hacemos `vagrant init vagrant-jessie` y para empezar a usar la máquina virtual usamos `vagrant up`. 
Con ello, Virtual Box arrancará la máquina a la cual se podrá uno conectar por medio de `vagrant ssh`.

Tras crear la máquina pasamos a provisionarla insertando el siguiente comando `vagrant provision`.


##Ejercicio 2
####Instalar una máquina virtual ArchLinux o FreeBSD para KVM, otro hipervisor libre, usando Vagrant y conectar con ella. 


##Ejercicio 3
####Crear un script para provisionar `nginx` o cualquier otro servidor web que pueda ser útil para alguna otra práctica


##Ejercicio 4
####Configurar tu máquina virtual usando `vagrant` con el provisionador ansible

