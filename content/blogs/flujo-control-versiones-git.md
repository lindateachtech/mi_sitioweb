---
author: lindateachtech
date: "2026-10-15"
description: "Si ya conectaste RStudio con GitHub desde la consola, aquí tienes la misma configuración pero con el paquete usethis de R, que automatiza cada paso: configurar Git, crear tu token de GitHub y conectar un proyecto nuevo o uno que ya existe."
draft: false
image: /images/r_github/commit.png
tags:
- rstudio
- git
- github
- usethis
- control de versiones
- tutorial
- intermedio
title: "¿Cómo conectar RStudio con GitHub usando el paquete usethis?"
toc: TRUE
---


El primer curso de Git que tomé fue hace casi cuatro años, un curso dirigido a programadores cuya metodología era aprender Git memorizando comandos, como quien memoriza un conjuro, escribía `git add`, `git commit`, `git push` en ese orden porque supuestamente así funcionaba, pero yo no tenía ni idea de qué estaba pasando por dentro ni por qué eran tres pasos y no uno. 

Luego, cuando aprendí control de versiones con The Carpentries, vi el flujo explicado de forma gráfica por primera vez, y pensé, dios mío, ¿es esto? Así es como debí aprenderlo desde el principio. A mí me funciona aprender de forma visual, y claramente no soy la única, porque ese mismo principio es la base de cómo Software Carpentry enseña control de versiones, un archivo que pasa por cuatro lugares distintos, tu carpeta, el área de staging, tu repositorio local y GitHub, y cada comando simplemente lo mueve de un lugar al siguiente. Una vez que tienes ese mapa en la cabeza, los comandos dejan de ser un conjuro y se vuelven lógicos.

Ese mapa del flujo lo he construido para mis talleres y puedes recorrerlo sin miedo a romper nada en el [simulador](/blogs/simulador-flujo-control-de-versiones) de flujo de trabajo de control de versiones. Sin embargo, la idea es ir un paso más allá del mapa conceptual y trabajarlo directamente en RStudio, y para eso utilizamos un paquete de R que automatiza buena parte de esta configuración y del trabajo con Git, el paquete `usethis`.

<img src="/images/r_github/usethis-hex.png" alt="Logo hexagonal del paquete usethis de R" style="max-width:140px; float:left; margin: 0 1.3em 0.8em 0;">

`usethis` es un paquete de Posit (antes RStudio) pensado para automatizar tareas repetitivas al crear y mantener proyectos de R, y cada función `use_*()` hace una sola cosa muy concreta, desde crear un archivo hasta configurar tu token de GitHub, en vez de tener que recordar el comando exacto para cada paso.

A continuación realizaremos paso a paso la configuración de Git y GitHub, conectaremos GitHub a un proyecto nuevo de RStudio y conectaremos GitHub a un proyecto que ya existe.

<div style="clear:both;"></div>

<br>

## Configuración de Git y GitHub

Esto se hace una sola vez por computadora, no por proyecto. Antes de cambiar nada, `git_sitrep()` te da un diagnóstico de cómo está tu configuración actual, si ves cruces en lugar de marcas de verificación junto a tu nombre, tu correo o tu token de GitHub, es que todavía falta configurarlos.

```r
usethis::git_sitrep()
```

**1. Dile a Git quién eres.** El correo debe ser el mismo con el que te registraste en GitHub.

```r
usethis::use_git_config(
  user.name = "Tu Nombre",
  user.email = "tu@correo.com"
)
```

**2. Crea un token de acceso personal en GitHub.**

```r
usethis::create_github_token()
```

Esto abre GitHub con los permisos ya marcados, solo tienes que elegir una fecha de caducidad (por ejemplo 90 días) y pulsar *Generate token*. El token se muestra una sola vez, cópialo antes de salir de esa pantalla.

**3. Guarda el token en tu computadora.**

```r
gitcreds::gitcreds_set()
```

Pega el token cuando te lo pida y pulsa Enter. Queda guardado en el gestor de credenciales de tu sistema operativo, y RStudio no te lo volverá a pedir.

**4. Vacuna tu `.gitignore` global.**

```r
usethis::git_vaccinate()
```

Esto agrega a todos tus proyectos una lista de archivos que Git debe ignorar siempre, entre ellos `.Rhistory`. Sin esta vacuna, si haces `git add .` en un proyecto, ese archivo podría subirse a GitHub con tu token incluido, porque `.Rhistory` guarda el historial de comandos que ejecutaste en la consola. GitHub suele detectar y bloquear tokens expuestos, pero no conviene depender de eso.

**5. Usa `main` como rama por defecto.**

```r
usethis::git_default_branch_configure()
```

**6. Comprueba que todo quedó bien.**

```r
usethis::git_sitrep()
```

Si ahora ves tu nombre, tu correo y el token como válidos, la configuración quedó lista, y no vuelves a repetir este bloque salvo que cambies de computadora.

<br>

## Cómo conectar GitHub a un proyecto nuevo


**1. Crea el repositorio en GitHub.** En github.com, pulsa el signo + de la esquina superior derecha y elige *New repository*. Dale un nombre (por ejemplo `mi-primer-repo`), márcalo como público, y activa las casillas *Add a README file* y *.gitignore* con la plantilla de R. El README es la portada del proyecto, y el `.gitignore` evita que subas sin querer archivos sensibles: mientras un archivo esté en esa lista, Git lo ignora al hacer commit.


**2. Tráelo a RStudio.** En GitHub pulsa el botón verde *Code* y copia la URL HTTPS. En RStudio ve a *File > New Project > Version Control > Git*, pega la URL y crea el proyecto. A esto se le llama clonar un repositorio: RStudio descarga todo lo que había en GitHub (el README y el `.gitignore`) y lo abre como proyecto nuevo. Verás aparecer la pestaña Git en el panel superior derecho.


**3. Agrega un script.** Crea un archivo nuevo (*File > New File > R Script*) con algo como:

```r
# Ventas ficticias por región de Ecuador
ventas <- data.frame(
  region = c("Costa", "Sierra", "Amazonía", "Galápagos"),
  ventas = c(1250, 980, 310, 140)
)
```

Guárdalo como `analisis.R`. Guardar el archivo no equivale a hacer `git add` ni `git commit`, pero en cuanto lo guardas, Git empieza a rastrear ese cambio y lo verás aparecer en la pestaña Git.

**4. Haz tu primer commit.** En la pestaña Git marca la casilla *Staged* de los archivos que quieras incluir y pulsa *Commit*. Marcar *Staged* equivale a `git add`, todavía no se ha guardado nada en el historial. En la ventana que se abre, escribe un mensaje descriptivo, por ejemplo "Añade tabla de ventas por región", y pulsa *Commit*. El mensaje importa porque es lo que te ayudará a encontrar esa versión si más adelante necesitas volver a ella.

**5. Sube los cambios con push.** Hasta aquí todo queda guardado solo en tu computadora. Para que se vea en GitHub, pulsa la flecha verde de *Push*. Si refrescas el repositorio en GitHub, verás los archivos subidos.

**6. Modifica el script y repite el ciclo.** Por ejemplo, agrega al final:

```r
barplot(ventas$ventas, names.arg = ventas$region,
        main = "Ventas por región", col = "#3c8b91")
```

Guarda, marca *Staged*, escribe un mensaje como "Añade gráfico de barras" y vuelve a hacer *Push*. Si comparas el archivo en GitHub, verás resaltadas en verde las líneas que agregaste, eso es un *diff*.

**7. Trae cambios remotos con pull.** Si alguien más modifica el repositorio (o lo haces tú mismo desde la web de GitHub, por ejemplo editando el README), esos cambios no aparecen automáticamente en tu computadora. Antes de empezar a trabajar, y sobre todo si colaboras con más personas, conviene pulsar la flecha azul de *Pull* para traer la última versión antes de hacer tus propios cambios.

**8. Revisa el historial.** El botón con el ícono de reloj en la pestaña Git abre el historial de commits. Al hacer clic en uno de ellos puedes ver exactamente qué líneas cambiaron, el mismo tipo de comparación que puedes practicar en el simulador.

<br>

## Cómo conectar GitHub a un proyecto existente

Si ya tienes un proyecto en RStudio que nunca pusiste bajo control de versiones, no hace falta recrearlo desde GitHub, puedes versionarlo donde está. Antes de empezar, revisa que la carpeta no tenga datos sensibles ni contraseñas: el primer commit sube todo lo que haya ahí dentro.

**1. Activa Git en el proyecto.**

```r
usethis::use_git()
```

Te preguntará si puede hacer un primer commit con los archivos que ya tiene el proyecto, y luego si puede reiniciar RStudio para activar la pestaña Git. En ambos casos conviene responder que sí. Al volver a abrir el proyecto, verás la pestaña Git disponible.

**2. Súbelo a GitHub.**

```r
usethis::use_github()
```

Esta función crea el repositorio en tu cuenta de GitHub, sube todo tu historial local y abre la página del repositorio en el navegador, usando el token que configuraste en el primer bloque.

<br>

## Taller

Todo este código puedes verlo en práctica en el taller de control de versiones con Git y GitHub que di en el mes de octubre de 2026, donde además de practicar el flujo vemos cómo conectarlo con tus propios proyectos de R y RStudio. También puedes encontrar el material que utilicé en este Taller en el siguiente [enlace](/cursos/see-rstudio-github) y la grabación en este video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/lcHvfmAEJso?si=yKMvDO7fIYT4k_69&amp;start=7450" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

