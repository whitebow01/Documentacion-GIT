# GIT [Revisar documentacion](https://git-scm.com/book/es/v2) 
***
## Comandos Basicos Linux
| Comando | Utilidad | 
| -- | -- | 
| ls | Ver el contenido del directorio en el que se encuentra el prompt. | 
| cd directorio | Acceder al directorio. | 
| cd .. | Un paso atras del promp. | 
| pwd | Revisar donde estamos ubicados. | 
| mkdir nomrbecarpeta | Crear carpeta.|
| touch nombrefichero.py, js, html, css, etc  | Crear archivos vacíos y cambiar marcas de tiempo de archivos o carpetas|
| mv archivo.txt /ruta/de/destino | Mover archivos a directorios o carpetas |
| cat | Imprime por pantalla el fichero seleccionado |
| rm nombrearchivo | Eliminamos el archivo|
>Tambien se puede utilizar `ls` con el nombre de un directorio para ver el contenido.

***
## Indentificadores de colores
**Indentificador de colores, segun tipo de archivo/elemento:**
| Color | Referencia | 
| -- | -- | 
| Color azul | Carpetas | 
| Color verde | Archivos ejecutables | 
| Color azul celeste | Carpetas especiales de Windows | 
| Color blanco | Archivos (pdf, jpg, doc, md, js, etc.) | 
***

## Repositorio


### Comandos repositorio local (git) : 
>Normalmente mas usados:

Iniciar un repositorio local:
~~~
git init 
~~~
Agrega el repositorio a ***"STAYING AREA"***. "Por Confirmar" para luego transformarlo en un **COMMIT** (versión):
~~~
git add <archivo> 
~~~
O (si queremos agregar todos los cambios de todos los archivos del **Directorio** actual a ***"STAYING AREA"***):
~~~
git add . 
~~~
Agregar la versión al repositorio. (**-m = mensaje**):
~~~
git commit -m "mensajedeconfirmación" <archivo>
o 
git commit -a -m "amensajedeconfirmación"
~~~
Al agregar `-a` no es necesario hacer un `add .` antes. Se salta el area de preparacion.

### GitHub
Para subir los archivos al servidor Remoto debemos pasar por los estados de  **ADD** y **COMMIT**. (Comprobar con `git status`)

Para subir los cambios a **GITHUB** :
~~~
git push origin main
~~~
Nos pedira Clave o Key en ciertas ocasiones.