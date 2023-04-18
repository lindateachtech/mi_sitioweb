---
author: lindajzmin
date: "2023-04-02"
description: ""
draft: false
image: /images/instalacion_r_rstudio.png
tags:
- rprogramming
- rstudio
- instalacion
- tutorial
title: ¿Cómo instalar R y RStudio?
toc: FALSE
---

> No se puede hacer data science desde una interfaz de usuario. </p>
> — <cite>Hadley Wickham[^1]</cite>


[^1]: Hadley Wickham es un estadístico de Nueva Zelanda y científico jefe de [Posit, PBC](https://posit.co/) (anteriormente RStudio Inc.) y profesor adjunto de estadística en la Universidad de Auckland. Es mejor conocido por su desarrollo de software de código abierto para el lenguaje de programación estadística R para visualización de datos, que admiten un enfoque de datos ordenados para la ciencia de datos.

Bienvenidas a todas las personas interesadas en aprender sobre la programación en R. Al instalar y configurar adecuadamente R y RStudio, podrás aprovechar al máximo su potencial y acelerar tu proceso de aprendizaje en el análisis de datos y la ciencia de datos.

Es importante tener en cuenta que R y RStudio son dos herramientas distintas, pero que trabajan en conjunto para crear un entorno óptimo para la programación en R.

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/r_rstudio.png" width="650px">
</p>
</div>

Primero, tenemos que instalar R, este es el lenguaje de programación y un entorno para programar. Y luego, instalamos RStudio que es un Entorno de Desarrollo Integral que ofrece una interfaz amigable para trabajar con R. RStudio nos proporciona una consola para escribir y ejecutar código, además de funciones adicionales como autocompletado de código, ayuda y debugging.

En este tutorial, nos centraremos en la instalación de ambas herramientas y cómo dejarlas operativas para iniciar a programar. Si eres nuevo en este tema, ten por seguro que este es un gran punto de partida para iniciar tu viaje en el mundo de la programación en R.


## Instalación de R

Empezamos con la descarga e instalación de R, para lo cual, nos dirigimos a la siguiente dirección [https://posit.co/download/rstudio-desktop/](https://posit.co/download/rstudio-desktop/) donde encontraremos los instaladores tanto de R como de RStudio.

Nos aparecerá la siguiente pantalla, aquí haremos clic en la opción que dice _“Download and Install R”_, y esto nos llevará al CRAN[^2]. 

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/rstudio_desktop.png" width="750px">
</p>
</div>

En el CRAN, elegimos el sistema operativo de nuestro ordenador. En este caso, hacemos click en la opción que dice _R para Windows_, y en la siguiente pantalla que nos aparece elegimos la primera opción que dice _base_. En este momento nos aparece el instalador de la última versión de R y hacemos clic para iniciar la descarga.

[^2]: CRAN es una red de servidores _ftp_ y _web_ en todo el mundo que almacenan versiones idénticas y actualizadas de código y documentación para R.

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/descarga_r.png" width="750px">
</p>
</div>

Cuando se haya terminado de descargar el instalador, abrimos el ejecutable, y damos los permisos para que inicie el proceso del asistente de instalación de R.

1. Elegimos el idioma _Español_ para la instalación de R y hacemos clic en el botón "Aceptar".

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/01_idioma.png" width="250px">
</p>
</div>

2. Luego nos aparecen los términos de la instalación del software, los leemos y hacemos clic en "Siguiente".

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/02_info.png" width="450px">
</p>
</div>

3. En esta parte, elegimos la carpeta de destino para la instalación de R, podemos dejar la que nos aparece que es en el disco C, o si desean cambiarlo pueden hacer clic en el botón "Examinar ..." y buscar la carpeta que deseen. Asegúrense que la dirección no contenga caracteres especiales como palabras con tildes u otros signos. Hacemos clic en "Siguiente".

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/03_carpeta.png" width="450px">
</p>
</div>

4. Luego, seleccionamos los componentes que deseamos instalar, se recomienda que mantengan los que se señalan por defecto. Hacemos clic en "Siguiente". Después, indicamos que NO deseamos utilizar las opciones de configuración. Otra vez hacemos clic en "Siguiente".

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/04_comp_conf.png" width="900px">
</p>
</div>

5. Mantenemos la carpeta del menú inicio en R. Hacemos clic en "Siguiente". Luego, seleccionamos las tareas adicionales, esto es si queremos crear accesos directos, guardar número de versión y asociar archivos `.RData` a R. Otra vez hacemos clic en "Siguiente".

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/05_menu_tareas.png" width="900px">
</p>
</div>

6. Esperamos unos segundos mientras se instala R y cuando se haya completado la instalación, cerramos la ventana dando clic en "Finalizar".

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/06_r-instalado.png" width="900px">
</p>
</div>

En este momento puedes hacer una prueba para confirmar que la instalación se hizo correctamente.


## Instalación de RStudio

Una vez que tengamos R instalado en nuestros ordenadores, regresamos a la página de [Posit, PBC](https://posit.co/) y ahora procederemos a descargar RStudio. Posit reconoce automáticamente nuestro sistema operativo y nos propone el instalador adecuado.

Hacemos clic en el ejecutable que se ha descargado e iniciamos la instalación de RStudio siguiendo todos los pasos que vienen por defecto, damos clic en "Siguiente". Tener en cuenta que la ruta de instalación no contenga caracteres especiales.

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/07_directorio.png" width="900px">
</p>
</div>

Luego de elegir la carpeta del menú Inicio, inicia la instalación lo que tomará unos dos minutos aproximadamente.

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_r/08_instalacion.png" width="900px">
</p>
</div>

Cuando se haya terminado la instalación hacemos clic en "Terminar". En el menú de aplicaciones del ordenador nos aparecerá un nuevo ícono de RStudio. Con esto, ya tenemos listo nuestro entorno de desarrollo integral para trabajar. 

También puedes visualizar el procedimiento de instalación de R y RStudio en el siguiente video tutorial.


## Youtube: Tutorial para la instalación paso a paso de R y RStudio

<br>
{{< youtube wM6K81wm2jQ >}}
<br>


