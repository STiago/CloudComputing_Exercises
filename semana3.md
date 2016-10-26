##Ejercicio 1
####Buscar una aplicación de ejemplo, preferiblemente propia, y deducir qué patrón es el que usa. ¿Qué habría que hacer para evolucionar a un patrón tipo microservicios?
   La aplicación buscada se corresponde a la realizada para un proyecto de una organización. Consiste en un sistema de gestión de experimentos donde estan identificados tres tipos de usuarios diferenciados por sus funciones, estos son: administrador, consultores de los datos y desarrolladores.
La plataforma permite a los desarrolladores publicar sus experimientos en el subgrupo al que pertenecen dentro del experimento que les corresponda a cada uno, los usuarios consultores solo tienen acceso a visualizar los datos obtenidos de la compilación de los experimentos. El administrador es el encargado de hacer la supervisión de estos, gestionar permisos y demás.

[Imagen](https://github.com/STiago/Pictures/blob/master/t3e1.png)

El patron que se identifica en este proyecto es el modelo cliente-servidor.

   Lo que se debería de realizar para evolucionar a un patrón tipo microservicios es por ejemplo hacer una abstracción de los servicios que da la aplicación para posteriormente desplegarlos en la nube.
Se podría abstraer el servicio que da la DB para desplegarlo de forma independiente, también se podría localizar como un servicio por ejemplo la subida de los documentos donde se muestran los resultados de las compilaciones de los experimentos, también la alta de usuarios, etc.
Finlamente, para obtener la arquitectura de microservicios, cuando tengamos especificados todos los servicios, los comunicaremos unos con otros por medio de una API REST.


##Ejercicio 2
####En la aplicación que se ha usado como ejemplo en el ejercicio anterior, ¿podría usar diferentes lenguajes? ¿Qué almacenes de datos serían los más convenientes?
En la app anterior se ha usado python pero se podrían usar distintos lenguajes.
Si la hubiesemos desarrollado con una arquitectura de microservicios se podría implementar cada servicio con el lenguaje más óptimo para cada uno.


