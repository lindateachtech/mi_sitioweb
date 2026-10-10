---
author: lindateachtech
date: "2026-10-15"
description: "Cuando empecé a aprender Git memorizaba comandos sin entender qué pasaba por dentro. Ahora que enseño control de versiones en talleres de Software Carpentry, construí una herramienta interactiva para que mis estudiantes entiendan el flujo completo desde el primer día."
draft: false
image: /images/r_github/commit.png
tags:
- git
- github
- control de versiones
- docencia
- software carpentry
- principiantes
title: "Memorizar comandos de Git y no entender nada"
toc: TRUE
---


El primer curso de Git que tomé fue hace casi cuatro años, un curso dirigido a programadores cuya metodología era aprender Git memorizando comandos, como quien memoriza un conjuro, escribía `git add`, `git commit`, `git push` en ese orden porque supuestamente así funcionaba, pero yo no tenía ni idea de qué estaba pasando por dentro ni por qué eran tres pasos y no uno. 

Luego, cuando aprendí control de versiones con The Carpentries, vi el flujo explicado de forma gráfica por primera vez, y pensé, dios mío, ¿es esto? Así es como debí aprenderlo desde el principio. A mí me funciona aprender de forma visual, y claramente no soy la única, porque ese mismo principio es la base de cómo Software Carpentry enseña control de versiones, un archivo que pasa por cuatro lugares distintos, tu carpeta, el área de staging, tu repositorio local y GitHub, y cada comando simplemente lo mueve de un lugar al siguiente. Una vez que tienes ese mapa en la cabeza, los comandos dejan de ser un conjuro y se vuelven lógicos.

Con el tiempo quise ir un poco más allá. Hay buenos recursos visuales sobre Git, pero casi todos están en inglés, y yo quería uno propio, pensado para mis estudiantes. Por eso creé esta herramienta interactiva, para enseñar el flujo de forma dinámica y que puedan ver en tiempo real cómo va cambiando el estado de cada archivo, en vez de imaginárselo.

Desde 2021 soy instructora de Software Carpentry y uso este material en mis talleres de control de versiones. Aquí te cuento los puntos donde más he visto trabarse a quienes están aprendiendo, los mismos donde yo me trababa, y al final te dejo el enlace al [simulador](/blogs/simulador-flujo-control-de-versiones) para que lo pruebes tú mismo.

## El área de staging es la primera pared

Lo que más cuesta no es Git en sí, es entender por qué existe un paso intermedio entre editar un archivo y guardarlo en el historial. En casi cualquier otra herramienta que usamos a diario (Word, Google Docs, incluso RStudio al guardar un script) el flujo es editar y guardar, sin pasos de más. Git te pide marcar primero qué cambios quieres incluir en la próxima foto del proyecto, y ese "paso de más" se siente innecesario hasta que lo necesitas, por ejemplo cuando cambiaste dos cosas distintas en un mismo script y quieres separarlas en dos commits con mensajes diferentes. Mientras no lo has necesitado, el staging parece burocracia.

## Confundir guardar con compartir

El segundo punto donde veo trabarse a casi todo el grupo es la diferencia entre hacer commit y hacer push. Es muy común que alguien haga su primer commit, se sienta satisfecho y luego pregunte por qué su compañero no ve el cambio. El commit guarda en tu historial local, push lo copia a GitHub para que otros lo vean. Son dos verbos distintos para dos lugares distintos, y en la cabeza de quien empieza, "guardar" es una sola acción. Cuando lo explico con el commit como una fotografía que guardas en tu álbum personal y el push como subir esa foto a un álbum compartido, el concepto suele aterrizar mejor que con cualquier definición técnica.

## El primer conflicto da pánico

El tercer momento, y el más intenso que recuerdo, fue mi primer conflicto de fusión en un proyecto real de trabajo. Hasta ese punto todo había sido lineal y previsible, edito, hago commit, hago push, y todo avanza. De pronto Git me dijo que había cambios que no sabía cómo combinar, y apareció un archivo lleno de símbolos raros. Mi primera reacción fue pensar que había roto algo, cuando en realidad Git estaba siendo cuidadoso, prefiere parar y preguntar antes que decidir por ti cuál versión es la correcta. Resolver ese primer conflicto sin perder nada me quitó buena parte del miedo para los siguientes.

## Una forma de practicar sin miedo

Explicar estos conceptos con diapositivas ayuda, pero lo que realmente los fija es ver el flujo completo moverse: un archivo que pasa de la carpeta de trabajo al staging, de ahí al repositorio local y finalmente a GitHub, con el historial creciendo en tiempo real. Armé esta herramienta interactiva para eso. Tiene una historia guiada que recorre paso a paso el ciclo completo, incluido un conflicto real entre tu computadora y GitHub, y un modo de práctica libre para que experimentes por tu cuenta sin ningún riesgo, porque aquí no hay ningún repositorio real detrás.

Puedes probarla en [el simulador de flujo de trabajo de control de versiones](/blogs/simulador-flujo-control-de-versiones). Te recomiendo empezar por la historia guiada para ver el ciclo completo una vez, y después pasar a práctica libre e intentar provocar tú mismo un conflicto, antes de probarlo en un repositorio real.

## Este material es parte de mi taller

Esta herramienta es una pequeña parte de lo que cubro en mi taller de control de versiones con Git y GitHub, donde además de practicar el flujo vemos cómo conectarlo con tus propios proyectos de R y RStudio. Si quieres profundizar, en [la página del taller](/cursos/control-versiones-git) tienes el material completo, las diapositivas y el repositorio de cada sesión, para que puedas revisarlo a tu ritmo o seguirlo paso a paso.

