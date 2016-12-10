#Ejercicios semana 9 - Orquestación de máquinas virtuales

##Ejercicio 1
####Instalar una máquina virtual Debian usando Vagrant y conectar con ella.

En primer lugar descargamos la máquina virtual de Debian usando vagrant con el siguiente comando:

`vagrant box add debian-jessie https://atlas.hashicorp.com/ARTACK/boxes/debian-jessie`

![Ejercicio 1](https://github.com/STiago/Pictures/blob/master/orquestacion1.png)

Seguidamente hacemos `vagrant init vagrant-jessie`.

![Ejercicio 1](https://github.com/STiago/Pictures/blob/master/orquestacion2.png)

Para empezar a usar la máquina virtual usamos `vagrant up`. 

![Ejercicio 1](https://github.com/STiago/Pictures/blob/master/orquestacion3.png)

Con ello, Virtual Box arrancará la máquina a la cual se podrá uno conectar por medio de `vagrant ssh`.

Tras crear la máquina pasamos a provisionarla insertando el siguiente comando `vagrant provision`.


##Ejercicio 2
####Instalar una máquina virtual ArchLinux o FreeBSD para KVM, otro hipervisor libre, usando Vagrant y conectar con ella. 


##Ejercicio 3
####Crear un script para provisionar `nginx` o cualquier otro servidor web que pueda ser útil para alguna otra práctica.
En primer lugar, editamos el fichero ***Vagrantfile*** dejandolo como se muestra a continuación:

``` 
 # -*- mode: ruby -*-
 # vi: set ft=ruby :

 Vagrant.configure("2") do |config|
 config.vm.box = "victoria"
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end
  config.vm.provision "shell",
    inline: "sudo apt-get install -y nginx && sudo service nginx restart && sudo service nginx status"

 end
``` 

Tras realizas las modificaciones anteriores, ejecutamos en nuestra máquina `vagrant provision` y con ello se ejecutan los comandos que se van a aprovisionar.

![Ejercicio 3](https://dl.dropbox.com/s/tecldglnf22x481/ejejerciio7.png)


##Ejercicio 4
####Configurar tu máquina virtual usando `vagrant` con el provisionador ansible.
Comenzamos la configuración añadiendo en el fichero ansible_host la IP de nuestra máquina como se muestra a continuación:

```
[vagrant]
192.168.1.36
```
El siguiente paso es indicarle a Ansible que tiene que usar este fichero usando `export ANSIBLE_HOSTS=~/ansible_hosts` y posteriormente introduciendo la linea `config.vm.network :private_network, ip: "192.168.1.36" ` con una IP desde la que podamos acceder desde nuestro ordenador todo ello en el fichero Vagrantfile.

Ahora, nos creamos el playbook para que Ansible que nos instale en la máquina Nginx como hemos visto se ha hecho en los ejercicios del tema 6.

A continuación, procedemos a aprovisionar la máquina al igual que hemos hecho en el ejercicio anterior, lanzando por línea de comandos:

`vagrant provision`

![Ejercicio 4](https://dl.dropbox.com/s/rtrqp4xlw9vsf1s/ejercicio8_tema6_3.png)

Y ya finalmente, solo queda acceder a nuestro navegador introduciendo la IP y veremos como nos muestra Nginx funcionando correctamente.



