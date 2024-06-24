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
Cuando empezamos en un nuevo equipo, necesitamos iniciar sesion en git para poder sincronizar con github o algun sv remoto

~~~
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
~~~

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

Sincronizar tu rama local con la rama remota
~~~
git pull origin ramaquequeremostraer(normal main)
~~~
### ERRORES CON GIT CLONACIONES
Cuando tenemos el error Permission denied (publickey) al intentar clonar o sincronizar los archivos a github. Indica que Git no puede autenticar tu conexión SSH con GitHub.

Lo mas rapido es crear otra clave ssh

1. En terminal:
~~~
ssh-keygen -t ed25519 -C "tuemail@example.com"
ssh-keygen -t rsa -b 4096 -C "tuemail@example.com"
~~~
Sigue las instrucciones:

Cuando te pida "Enter a file in which to save the key", presiona Enter para aceptar la ubicación predeterminada (/home/tu_usuario/.ssh/id_ed25519 o /home/tu_usuario/.ssh/id_rsa).

Introduce una frase de paso (opcional pero recomendado) y confírmala.

2. Agregar la clave SSH al agente SSH
~~~
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
~~~

3. Añadir la clave SSH a tu cuenta de GitHub
~~~
cat ~/.ssh/id_ed25519.pub
~~~
Copia el contenido de la clave pública mostrada en la terminal.

4. Agregar la clave SSH a GitHub:

    Ve a GitHub Settings.
    Haz clic en New SSH key.
    Introduce un título descriptivo para la clave y pega la clave pública copiada.
    Haz clic en Add SSH key.
5. Ahora intenta clonar lo que deseas clonar. Te pedira la clave que pusiste anteriormente

### Revisar el Estado de tus Archivos
Revision **ESTADO** general del repositorio:
~~~
git status 
o
git status -s  
~~~
`-s` solamente muesta los ficheros en los cuales hubieron cambios y el estado en el que se encuentran.
>El comando te indica en cuál rama estás y te informa que ha variado con respecto a la misma rama en el servidor.
Tambien podemos usar 
~~~
git diff 
~~~
Este comando muestra las líneas exactas que fueron añadidas y eliminadas.

1. Revisaremos si se hicieron los cambios con `git status`.
***
### Historial se Confirmaciones
#### Git log
1. Luego revisaremos la version de commit con su identificador unico o **HASH** con su respectiva informacion:
~~~
git log 
o
git log --oneline
~~~
>El mecanismo que usa Git para generar esta suma de comprobación se conoce como hash SHA-1. Se trata de una cadena de 40 caracteres hexadecimales (0-9 y a-f), y se calcula con base en los contenidos del archivo o estructura del directorio en Git. Por ejemplo:
~~~
24b9da6552252987aa493b52f8696cd6d3b00373
~~~
>Git guarda todo no por nombre de archivo, sino por el valor hash de sus contenidos.

Tambien se puede hacer variantes de `git log` como :

| Comando log | Funcion | 
| -- | -- | 
| -p | Muestra las diferencias introducidas en cada confirmación. | 
| -2 | Se muestren únicamente las dos últimas entradas del historial. | 
| -p -2 | Diferencias y ultimas entradas del hitorial. | 
| --stat: | Estadísticas de cada confirmación. | 


#### Git log en ramas
git puede mostrar las versiones de rammas por separado. Distinto a git log que muestra todo el historial del proyecto.

[Ver mas sobre git en ramas](https://es.stackoverflow.com/questions/496506/como-mostrar-el-log-de-una-rama-espec%C3%ADfica-de-git-sin-mostrar-la-rama-master) 

Mostrar commits que hay en una rama pero en las otras no:
~~~
git log --oneline --graph master..ramaquequeremosverloscommits
~~~

### ERRORES COMUNES (O solo a mi):
Algunas veces tengo cuando hago un git push origin main y no me deja subirlo. Me pide usuario y contrasena pero aun cuando son correcto me sale esto:
~~~
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Autenticación falló para 'https://github.com/
~~~

Aunque tengo claves ssh, me salio igual el error.
1. Entonces liste las claves que tengo:
`ls ~/.ssh   `

1. Luego  Agregar la Clave SSH al Agente SSH:
~~~
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
~~~
Agrega la que quieras del listado que te dio antes.

1. Luego Actualizar la URL Remota del Repositorio:
`git remote set-url origin git@github.com:tunombredeusuario/eldirectorioconelquetienesproblemas`

1. Probar la Conexión SSH con GitHub:
`ssh -T git@github.com`

1. Ahora podras hacer un `git push origin main`


#### Cambio de Correo Electrónico en Commits Anteriores en Git
Me paso que formatee mi equipo y luego instale git y puse otro correo que terminaba en .cl. Entonces cuando hacia git push, los cambios no se veian reflejados en mis graficos. Entonces tuve que actualizar el correo y los commits que ya habia hecho, ya los pude ver.

Para ver si es este el problema, veremos el log(historial de commits):`git log`.
Si los commits anteriores estan con un correo distinto al de github(a menos que lo hayas cambiado desde la app). Se debe hacer lo siguiente:

Entonces Reescribiremos el historial de commits para actualizar el correo en los commits anteriores.

**Pasos para Cambiar el Correo Electrónico en Commits Anteriores**

1. Configurar el Correo Electrónico Correcto para Futuros Commits

Asegúrate de que el correo electrónico correcto esté configurado globalmente o para el repositorio específico:
~~~
   git config --global user.email "tuemailcorrecto@example.com"
~~~
2. Reescribir el Historial de Commits

Utiliza este script para reescribir el historial de commits y cambiar el correo electrónico en los commits anteriores:

~~~
#!/bin/sh

git filter-branch --env-filter '
OLD_EMAIL="email_incorrecto@example.com"
CORRECT_NAME="TuNombre que tienes en github"
CORRECT_EMAIL="tuemailcorrecto@example.com"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
~~~

3. Forzar el Push al Repositorio Remoto
Este paso sobrescribirá el historial de commits en el remoto:
~~~
git push --force --tags origin 'refs/heads/*'
~~~

4. Confirmar los Cambios. Verificar el Nuevo Correo Electrónico
```
git config user.email
```

Verificar el Historial de Commits
`git log`



## ALGUNAS COSAS A TENER EN CUENTA EN GITHUB
Si hacemos una ramma adicional a la main-master con:
~~~
### Crear una nueva rama
git branch nueva-rama

### Cambiar a la nueva rama
git checkout nueva-rama
o
git switch nueva-rama

### Crear y cambiar a la nueva rama en un solo paso
git checkout -b nueva-rama
o
git switch -c nueva-rama

### Verificar en qué rama estás
git branch

### Hacer push de la nueva rama al repositorio remoto
git push origin nueva-rama
~~~
Luego si hacemos un git push origin nuevarama, esta no se vera en el grafico de commits en github, hasta que hagamos:

~~~
### Fusionar la nueva rama con la rama principal
git checkout main
git merge nueva-rama

### Eliminar la nueva rama
git branch -d nueva-rama
### o forzar eliminación
git branch -D nueva-rama
~~~

