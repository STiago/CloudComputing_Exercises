##Ejercicio 1
####Instalar una máquina virtual Debian usando Vagrant

Inicialmente, nos instalamos en nuestra máquina anfitriona vagrant usando:

`sudo apt-get install vagrant`

Tras instalarlo, procedemos a realizar los siguientes pasos:

`vagrant box add {title} {url}`
`vagrant init {title}`
`vagrant up`

Insertamos en consola la siguiente línea de comandos también:

`vagrant box add debian-jessie https://github.com/holms/vagrant-jessie-box/releases/download/Jessie-v0.1/Debian-jessie-amd64-netboot.box`

Y ya solo queda conectar a la máquina con ssh :

`vagrant ssh`


##Ejercicio 2
####Crear un script para provisionar `nginx` o cualquier otro servidor web que pueda ser útil para alguna otra práctica
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

![Ejercicio 7](https://dl.dropbox.com/s/tecldglnf22x481/ejejerciio7.png)



##Ejercicio 3
####Configurar tu máquina virtual usando `vagrant` con el provisionador ansible
Comenzamos la configuración añadiendo en el fichero ansible_host la IP de nuestra máquina como se muestra a continuación:

```
[vagrant]
192.168.1.36
```
El siguiente paso es indicarle a Ansible que tiene que usar este fichero usando `export ANSIBLE_HOSTS=~/ansible_hosts` y posteriormente introduciendo la linea `config.vm.network :private_network, ip: "192.168.1.36" ` con una IP desde la que podamos acceder desde nuestro ordenador todo ello en el fichero Vagrantfile.

Ahora, nos creamos el playbook para que Ansible que nos instale en la máquina Nginx como hemos visto se ha hecho en los ejercicios del tema 6.

A continuación, procedemos a aprovisionar la máquina al igual que hemos hecho en el ejercicio anterior, lanzando por línea de comandos:

`vagrant provision`

![Ejercicio 8](https://dl.dropbox.com/s/rtrqp4xlw9vsf1s/ejercicio8_tema6_3.png)

Y ya finalmente, solo queda acceder a nuestro navegador introduciendo la IP y veremos como nos muestra Nginx funcionando correctamente:

![Ejercicio 8](https://dl.dropbox.com/s/m226nqn6hmnnvq4/pant.png)




