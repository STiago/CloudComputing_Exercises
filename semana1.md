##Ejercicio 1
####Instalar alguno de los entornos virtuales de node.js y, con ellos, instalar la última versión existente, la versión minor más actual de la 0.12 y lo mismo para la 0.11 o alguna impar. Si no se usa habitualmente este lenguaje, hacer lo mismo con cualquier otro lenguaje de scripting.

Para la realización de este ejercicio he instalado el entorno virtual n ejecutando las siguientes ordenes :

```
git clone https://github.com/tj/n.git
cd n
sudo make install
```

![e1_i1](https://github.com/STiago/Pictures/blob/master/e1_i1.png)

Despues de haberlo instalado correctamente como se muestra en la captura anterior, pasamos a ver las versiones de Node.js que se pueden instalar ejecutando la siguiente línea:

```
sudo n ls
```

![e1_i2](https://github.com/STiago/Pictures/blob/master/e1_i2.png)

Procedemos a instalar la 0.11.16 y la versión 0.12.7 de la siguiente forma:

```
sudo n 0.11.16
sudo n 0.12.7
```

![e1_i3](https://github.com/STiago/Pictures/blob/master/e1_i3.png)


##Ejercicio 2

####Como ejercicio, algo ligeramente diferente: una web para calificar las empresas en las que hacen prácticas los alumnos. Las acciones serían crear empresa y listar calificaciones para cada empresa, crear calificación y añadirla (comprobando que la persona no la haya añadido ya), borrar calificación (si se arrepiente o te denuncia la empresa o algo) y hacer un ránking de empresas por calificación, por ejemplo. Crear un repositorio en GitHub para la librería y crear un pequeño programa que use algunas de sus funcionalidades. Si se quiere hacer con cualquier otra aplicación, también es válido.Se puede hacer un ejercicio equivalente, siempre que tenga operaciones similares: creación, listado, borrado, ciclo CRUD básico. El objetivo de este ejercicio es poner en práctica lo que viene a continuación, NO es un objetivo de la asignatura.


##Ejercicio 3

####Ejecutar el programa en diferentes versiones del lenguaje. ¿Funciona en todas ellas?


##Ejercicio 4

####Crear una descripción del módulo usando package.json. En caso de que se trate de otro lenguaje, usar el método correspondiente.


##Ejercicio 5
####Automatizar con grunt y docco (o algún otro sistema) la generación de documentación de la librería que se cree. Previamente, por supuesto, habrá que documentar tal librería.

Instalamos grunt instroduciendo en el terminal la siguiente línea:

```
sudo npm install -g grunt-cli
```

Después procedemos a crear el fichero Gruntfile.js indicando en el src los archivos .js de la raiz y del directorio lib puesto que estos son los los archivos de los que haremos la documentación.

Quedando como se muestra a continuación:

```
'use strict';
module.exports = function(grunt) {
   grunt.initConfig({
     pkg: grunt.file.readJSON('package.json'),
     docco: {
       debug: {
         src: ['*.js', 'lib/*.js'], //Los ficheros que hemos mencionado de la raiz y de lib
         options: {
           output: 'docs/'
         }
       }
     }
   });
   grunt.loadNpmTasks('grunt-docco'); //Cargamos grunt
   grunt.registerTask('default', ['docco']); //Hacemos la documentación
};
```
A continuación procedemos a la instalación de grunt-docco, docco, añadimos las dependencias devDependencies de package.json y finalmente pasamos a generar la documentación de la siguiente forma:

```
npm install docco grunt-docco --save-dev
grunt docco
```



##Ejercicio 6
####Para la aplicación que se está haciendo, escribir una serie de aserciones y probar que efectivamente no fallan. Añadir tests para una nueva funcionalidad, probar que falla y escribir el código para que no lo haga (vamos, lo que viene siendo TDD).


##Ejercicio 7
####Convertir los tests unitarios anteriores con assert a programas de test y ejecutarlos desde mocha, usando descripciones del test y del grupo de test de forma correcta. Si hasta ahora no has subido el código que has venido realizando a GitHub, es el momento de hacerlo, porque lo vamos a necesitar un poco más adelante.


##Ejercicio 8
####Ejercicio: Haced los dos primeros pasos antes de pasar al tercero..



