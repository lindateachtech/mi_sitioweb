---
author: lindajzmin
date: "2023-04-18"
description: ""
draft: false
image: /images/conectar_rstudio_gith.jpg
tags:
- rstudio
- github
- tutorial
- control de versiones
title: ¿Cómo conectar RStudio con GitHub?
toc: FALSE
---


> “¿Investigación científica libre? El segundo adjetivo es redundante”. </p>
> — <cite>Ayn Rand</cite>


La colaboración en equipo es fundamental para el éxito en cualquier proyecto, y esto es especialmente cierto en el ámbito de la investigación y el análisis de datos. Los equipos de investigación que colaboran de manera efectiva pueden lograr una mayor eficiencia y productividad, así como una mejor calidad de los resultados. En este sentido, Github es una especie de google drive pensado para la investigación reproducible, en donde cada proyecto es un repositorio. La mayoría de los investigadores que trabajan en investigación reproducible dejan todo su trabajo documentado en sus repositorios, lo cual permite interactuar con otros autores.

Al conectar RStudio a GitHub, los investigadores pueden trabajar juntos de manera más efectiva en sus proyectos de análisis de datos, manteniendo un historial detallado de los cambios realizados en el proyecto y asegurándose de que todos los miembros del equipo estén trabajando en la misma versión del código. 

En este tutorial te mostraré cómo conectar RStudio con GitHub para que aproveches al máximo esta poderosa herramienta de control de versiones. 

<br>

## Instalación de Git

Si es la primera vez que vas a utilizar GitHub, debes empezar por instalar Git, para lo cual, nos dirigimos a la siguiente dirección [https://git-scm.com/](https://git-scm.com/) donde haremos clic en el botón de `Downloads`.

<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/git1.png" width="600px">
</p>
</div>

Nos aparecerá la siguiente pantalla, aquí haremos clic en el sistema operativo de nuestro ordenador, en este caso hago clic en la opción de `Windows` y después nos aparecerá la ventana para descargar el instalador en la opción que dice _“Click here to download”_.

<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/git2.png" width="850px">
</p>
</div>

Esperamos unos segundos hasta que se haya terminado de descargar el instalador, y luego abrimos el ejecutable. Aquí se abrirá la ventana del asistente de instalación de Git, donde se nos mostrarán varios pasos y configuraciones para la instalación, sólo haremos clic en `Next` y escogeremos todas las opciones que nos recomiende el asistente por defecto hasta llegar a la instalación, y al finalizar haremos clic en `Finish`.


<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/git4.png" width="850px">
</p>
</div>


<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/git5.png" width="850px">
</p>
</div>

<br>

## Configuración de correo y usuario

Una vez que hayamos instalado Git, nos dirigimos a las aplicaciones de Windows y abrimos _"Git Bash"_ que es la consola de comandos de Git para configurar el correo electrónico y usuario. 

Para configurar el correo electrónico tecleamos el siguiente código en la consola de Git Bash: `git config --global user.email "lindajzmin@gmail.com"`. En esta parte deberán digitar su correo electrónico y debe ser el mismo correo con el que tengan la cuenta en GitHub. Así mismo, para configurar el usuario tecleamos el siguiente código en la consola de Git Bash: `git config --global user.name "lindajzmin"`, donde deberán introducir el respectivo usuario.


<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/config.png" width="450px">
</p>
</div>

<br>


## Configuración de Git en RStudio

El siguiente paso es configurar Git en Rstudio y crear la _SSH key_, para esto, abrimos RStudio, hacemos clic en la pestaña "Tools" de la Barra de Menú, y escogemos la opción “Global Options”. Se abrirá una ventana con un menú en la parte lateral izquierda y buscamos la opción “Git/SVN”.

En esta pantalla nos aseguramos que donde dice _Git executable_ se encuentre la ubicación del ejecutable que se guardó en nuestros ordenadores al momento que instalamos Git. En caso de que no aparezca el ejecutable, la dirección es: `C:\Program Files\Git\bin\git.exe`.

<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/gitsvn.png" width="850px">
</p>
</div>

Luego procedemos a crear una clave SSH, por lo que haremos click en el botón que dice “Create SSH Key…”. Aquí aparecerá una nueva ventana donde elegimos el tipo de llave `RSA` y pondremos una contraseña a esta llave creada. Hacemos clic en "Create" y nos aparecerá una ventana donde se confirma la generación de la llave RSA y la llave que es un código encriptado.

Cerramos esta ventana, y en la celda que dice "SSH key" ya nos aparece la opción "View public key". Tener en cuenta que este código lo necesitaremos más adelanre para agregarlo a GitHub. Para cerrar esta ventana hacemos click en "OK"."

<br>


## Añadir SSH key a GitHub

El siguiente paso es ligar esta llave a GitHub para que pueda conectar con RStudio. Para los que utilizan GitHub por primera vez, necesitan crear una cuenta en GitHub, en la siguiente dirección [https://github.com/login](https://github.com/login), aquí deben hacer clic en “Create a new account” y aparecerá una nueva ventana donde deben ingresar un correo electrónico, contraseña y usuario para crear la cuenta.

<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/login.png" width="850px">
</p>
</div>

Luego de crear la cuenta en GitHub, nos realizan una pregunta de verificación y nos envían un código al correo electrónico proporcionado. Una vez que confirme el código, GitHub le da la bienvenida y deberá contestar unas preguntas para completar su perfil, como cuántos miembros trabajarán con usted y si es un estudiante o profesor. ¡Y eso es todo! Tenemos cuenta en GitHub.
 
Ahora si, con nuestra cuenta de GitHub ya podemos agregar la _SSH key_ a GitHub, para esto, ingresamos a nuestra cuenta en [https://github.com/login](https://github.com/login) y hacemos clic en la esquina superior derecha del panel, donde se desplegará una lista de opciones, de la cual elegiremos la opción “Settings”. Se nos abrirá una ventana con un menú de opciones en la parte lateral izquierda, donde elegiremos la opción “SSH and GPG keys”. En esta pantalla hacemos clic en el primer botón verde que indica “New SSH key”.

<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/github.png" width="850px">
</p>
</div>

Al hacer clic en “New SSH key”, se abrirá una ventana donde debemos introducir un título para la _SSH key_, este se recomienda que sea un identificador del ordenador, y en la celda que dice "Key" debemos pegar la llave que generamos en RStudio, luego hacemos clic en el botón verde “Add SSH key”. Y tendremos la llave agregada a GitHub con los datos de título, fecha de creación y el código encriptado.

<div>
<p style = 'text-align:center;'>
<img src="/images/r_github/github2.png" width="850px">
</p>
</div>


<br>

## Youtube: Tutorial para la instalación paso a paso de R y RStudio

<br>
{{< youtube wM6K81wm2jQ >}}
<br>


