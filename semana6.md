##Ejercicio 1
####Instalar chef en la máquina virtual que vayamos a usar.
Procedemos a instalar chef con gem install ohai chef o simplemente ejecutamos en nuestra máquina la siguiente línea:

curl -L https://www.opscode.com/chef/install.sh | bash

comprobamos a continuación de que está instalado haciendo los siguiente:

![chef1](https://github.com/STiago/Pictures/blob/master/e1_t6.png)

##Ejercicio 2
####Crear una receta para instalar nginx, tu editor favorito y algún directorio y fichero que uses de forma habitual.

En primer lugar, creamos nuestra estructura de carpetas como solemos hacer (con el comando mkdir seguido del nombre que le vayamos a dar a los directorios), después dentro ya de nuestro directorio, procedemos a crearnos el archivo "default.rb" el cual contendrá nuestra receta.

```rb
package 'nginx'
package 'emacs'
directory '/home/STiago/GitHub'
file "/home/STiago/GitHub/LEEME.txt" do
  owner "stiago"
  group "stiago"
  mode 00544
  action :create
  content "Directorio"
end
```

El siguiente paso es crear en el nivel de chef el archibo en json y el archivo solo.rb (el primero refiere nuestra receta y el segundo indica donde está la receta y el archivo json, y además se encarga de ejecutar la receta)

Fichero json

```js
{
  "run_list":["recipe[nginx]"]
}
```

Fichero solo.rb

```rb
file_cache_path "/home/fblupi/chef"
cookbook_path "/home/fblupi/chef/cookbooks"
json_attribs "/home/fblupi/chef/node.json"
```

Seguidamente lanzamos la orden `sudo chef-solo -c chef/solo.rb`.


Ya estaría todo terminado, solo nos queda probar que la receta funciona y nos instala todo lo que hemos introducido en ella correctamente.

Todos los archivos creados se muestran en el siguiente árbol de contenidos.

![Ejercicio2](https://github.com/STiago/Pictures/blob/master/e2_t6.png)

##Ejercicio 3
####Escribir en YAML la siguiente estructura de datos en JSON

{ uno: "dos",
  tres: [ 4, 5, "Seis", { siete: 8, nueve: [ 10, 11 ] } ] }

En YAML sería de la siguiente forma:

> ```
> --- # 
>  tres:
>    - 4
>    - 5
>    - "Seis"
>    -
>      siete: 8
>      nueve:
>        - "Object"
>  uno: "dos"

> ---
> `


##Ejercicio 4
####Provisionar una máquina virtual en algún entorno con los que trabajemos habitualmente usando Salt.



##Ejercicio 5
####Desplegar los fuentes de la aplicación de DAI o cualquier otra aplicación que se encuentre en un servidor git público en la máquina virtual Azure (o una máquina virtual local) usando ansible.
El primer paso que tenemos que realizar es instalarnos Ansible en nuestra máquina anfitriona, primero añadiendo el repositorio, luego haciendo un update y finalmente instalando con `sudo apt-get install ansible` como se muestra a continuación:

![Ejercicio5](https://github.com/STiago/Pictures/blob/master/e5_t6.png)


Tras instalar Ansible, nos creamos el fichero ansible_host en el cual debemos de introducir las máquinas que vamos a controlar, en mi caso sería:

`[azure]`
`victoriasantiago.cloudapp.net`

![Ejercicio 4](http://ubuntuone.com/3k61J2ofJemgBsOovQpS7y)

A continuación, cambiamos el valor de ANSIBLE_HOSTS y hacemos un ping a nuestra máquina de Azure comprobando que nos conecta mediante ansible.

![Ejercicio 4](http://ubuntuone.com/5ODQV45JN9xwfutpFDzQ2S)

A continuación instalamos git en la máquina de azure y tras su instalación, ya en nuestra máquina anfitriona, procedemos a hacer el despliegue de los fuentes de nuestra aplicación de DAI como se muestra en la siguiente captura:

![Ejercicio 4](http://ubuntuone.com/7Wef1yaLAyYHJ9yP4p802U)

Finalmente, para ver que se ha realizado todo correctamente, basta con hacer en la máquina un ls o tree que nos muestre que el despliegue se ha llevado a cabo bien.

![Ejercicio 4](http://ubuntuone.com/4Ch1wWfQXFdzs6fgrHBMlo)


##Ejercicio 6
####Desplegar la aplicación de DAI con todos los módulos necesarios usando un playbook de Ansible.

En primer lugar, nos creamos el archivo playbook con extensión yml en el cual introducimos lo siguiente:

![Ejercicio 5](http://ubuntuone.com/4UaSuda6ZvE1pf8nrkhexu)

Seguidamente, en nuestra máquina anfitriona introducimos lo siguiente:

`export ANSIBLE_HOSTS=~/ansible_hosts`
`ansible-playbook playbook.yml --ask-pass -u victoria`

Quedando de la siguiente forma:

![Ejercicio 5](http://ubuntuone.com/14pxhjeWeBbmbrHWLWdhXm)


Y finalmente, abrimos nuestro navegador y podremos ver que nuestra aplicación se encuentra ejecutandose:

![Ejercicio 5](http://ubuntuone.com/0alDyvrQbLTdFcRmAWr7fS)



