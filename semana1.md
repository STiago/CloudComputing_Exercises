##Ejercicio 1
####Instalar alguno de los entornos virtuales de node.js y, con ellos, instalar la última versión existente, la versión minor más actual de la 0.12 y lo mismo para la 0.11 o alguna impar. Si no se usa habitualmente este lenguaje, hacer lo mismo con cualquier otro lenguaje de scripting.

Para la realización de este ejercicio he instalado el entorno virtual n ejecutando las siguientes ordenes :

```
git clone https://github.com/tj/n.git
cd n
sudo make install
```

![e1_i1](https://dl.drive.google.com/file/d/0B9EKMsCXU3CXYl9jUXBlS2tQS2c/view?usp=sharing/)

Despues de haberlo instalado correctamente como se muestra en la captura anterior, pasamos a ver las versiones de Node.js que se pueden instalar ejecutando la siguiente línea:

```
sudo n ls
```

![e1_i2](https://dl.drive.google.com/drive/folders/0B9EKMsCXU3CXN3QxNTdMbVhWNkU)

Procedemos a instalar la 0.11.16 y la versión 0.12.7 de la siguiente forma:

```
sudo n 0.11.16
sudo n 0.12.7
```

![e1_i3](https://dl.drive.google.com/file/d/0B9EKMsCXU3CXTEs0UG9ZRF9XR2M/view?usp=sharing)
