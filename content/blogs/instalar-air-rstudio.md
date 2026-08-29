---
author: lindateachtech
date: "2026-08-24"
description: "Qué es Air, el formateador de código R escrito en Rust, por qué mejora la legibilidad de tus scripts y cómo instalarlo y conectarlo con RStudio."
draft: false
image: /images/instalacion_air/instalacion_air.jpg
tags:
- rstudio
- air
- buenas prácticas
- tutorial
- principiante
title: Air, el formateador de código R que necesitas conocer
toc: TRUE
---


> “El código se lee muchas más veces de las que se escribe”. </p>
> — <cite>Guido van Rossum</cite>


¿Cuántas veces te ha pasado que abres un script de un compañero y tardas más en entender cómo está escrito que en entender qué hace? La indentación, los espacios, las líneas eternas que no caben en la pantalla... todo eso consume tiempo y energía que deberíamos dedicar a la parte importante del análisis.

Ahí es donde entra Air, un formateador de código R escrito en Rust que se encarga de la parte más tediosa de escribir código, la de darle una capa consistente y legible sin que tengas que pensar en ello. En este tutorial te cuento qué es, por qué merece la pena usarlo y cómo instalarlo y conectarlo con RStudio.

<br>

## Qué es Air y para qué sirve


Air es un formateador y también un language server para R. Un formateador no cambia el significado de tu código, únicamente se encarga de su presentación, indentación, saltos de línea, espacios alrededor de operadores y longitud de las líneas, siguiendo un conjunto de reglas basadas principalmente en la guía de estilo Tidyverse.
 
Por ejemplo, si escribes algo tan denso como esto:
 
```r
1+2:3*(4/5)
```
 
Air lo reformatea automáticamente así:
 
```r
1 + 2:3 * (4 / 5)
```
 
Y si tienes una expresión demasiado larga, Air la reorganiza en varias líneas para que no se salga del ancho recomendado (80 caracteres por defecto), respetando siempre la indentación de 2 espacios.
 
Usar un formateador como Air aporta dos ventajas muy claras. La primera es que te ahorra pensar en el estilo mientras escribes, porque Air lo resuelve por ti al guardar el archivo. La segunda es que reduce la fricción cuando trabajas en equipo, ya que todo el código que reciba tu compañero seguirá el mismo estándar, y las revisiones de código pueden centrarse en el contenido en lugar de en discutir estilos.
 
Air también incluye funciones útiles como el autobracing (añade automáticamente llaves `{}` a los `if`, bucles y funciones cuando hace falta para que el código sea portable) y los saltos de línea persistentes, que te permiten decidir tú, en ciertos puntos concretos, si quieres que una expresión se mantenga expandida en varias líneas.

<br>

## Instalación de Air

Para usar Air desde la línea de comandos, Posit ofrece instaladores independientes según tu sistema operativo.

Para el caso de Windows, desde PowerShell:

```powershell
powershell -ExecutionPolicy Bypass -c "irm https://github.com/posit-dev/air/releases/latest/download/air-installer.ps1 | iex"
```
Instalas AIR con el código anterior y el instalador añade Air a tu PATH automáticamente, aunque la primera vez necesitarás reiniciar la terminal para que el cambio se aplique.

<br>

## ¿Cómo conectar Air con RStudio?
 
RStudio todavía no soporta el Language Server Protocol, así que la conexión con Air se hace configurándolo como formateador externo. Antes de nada, comprueba que tienes al menos la versión 2024.12.0 de RStudio, y que ya has instalado Air siguiendo el paso anterior.
 
Una vez tengas ambas cosas listas, sigue estos pasos dentro de RStudio.
 
1. Abre `Tools -> Global Options -> Code`.
2. Ve a la pestaña `Formatting`.
3. Cambia la opción `Code formatter` a `External`.
4. En `Reformat command`, escribe la ruta a Air seguida de `format`, por ejemplo `{ruta/a/air} format`. Ten en cuenta que RStudio añadirá automáticamente el nombre del archivo al final del comando, tú solo tienes que indicar la ruta y la palabra `format`.
5. Para averiguar la ruta de Air en tu ordenador, ejecuta `where air` en el símbolo del sistema si usas Windows. Si la ruta contiene espacios, envuélvela entre comillas dobles, por ejemplo `"/Users/Tu Nombre/air" format`.
6. Marca la casilla `Reformat documents on save`, si quieres que Air se ejecute automáticamente cada vez que guardas un archivo.
7. Aplica los cambios y cierra la ventana de opciones.

<div>
<p style = 'text-align:center;'>
<img src="/images/instalacion_air/air_steps.png" width="900px">
</p>
</div>

A partir de aquí, las opciones `Reformat Selection` y `Reformat Document` ya usarán Air.

> Un detalle importante, es que Air todavía no funciona con documentos **Quarto** dentro de RStudio.



<br>

## Incorpóralo a tu flujo de trabajo

Más allá de RStudio, Air también se puede usar desde la línea de comandos para formatear archivos individuales o carpetas completas de forma recursiva, e incluso en modo `--check`, lo que lo hace perfecto para integrarlo en un hook de pre-commit de Git o en un workflow de GitHub Actions.
 
Esto cobra especial importancia cuando estás construyendo un paquete de R. En ese contexto no basta con que el código funcione, también debe seguir buenas prácticas de programación para que sea mantenible, fácil de revisar por otras personas y consistente a lo largo de todos los archivos del paquete. Tener un formateador como Air integrado en tu flujo evita que ese estándar dependa de la disciplina manual de cada colaborador, y hace que cualquier pull request se pueda revisar centrándose en la lógica del código y no en detalles de estilo.
 
Si trabajas en equipo, o simplemente quieres que tu código sea más legible sin esfuerzo extra, Air es una herramienta que vale la pena probar. Puedes consultar toda la documentación oficial en la [web de Air](https://posit-dev.github.io/air/).

