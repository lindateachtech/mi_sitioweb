---
author: lindateachtech
date: "2026-10-09"
description: "Herramienta interactiva para enseñar el flujo básico de control de versiones de forma dinámica: cubre add, commit, push y pull en un flujo lineal, para que puedan ver en tiempo real cómo va cambiando el estado de cada archivo, en vez de imaginárselo. Ramas y forks quedan para un siguiente simulador."
draft: false
image: /images/r_github/simulador.png
tags:
- git
- github
- rstudio
- control de versiones
- docencia
- simulador
- software carpentry
- principiantes
title: "Simulador del flujo básico de control de versiones (sin ramas)"
toc: TRUE
---


Esta es una herramienta interactiva para enseñar el flujo de trabajo de control de versiones de forma dinámica y que puedan ver en tiempo real cómo va cambiando el estado de cada archivo, en vez de imaginárselo. Este simulador cubre el flujo básico y lineal (sin ramas ni forks); esos temas quedan para un simulador aparte más adelante.


<div style="margin: 0 0 1.5em;">
<iframe id="git-flow-iframe" src="/interactive/flujo-control-versiones.html" style="width:100%; height:600px; border:1px solid #D3DBE6; border-radius:12px; display:block;" loading="lazy" title="Flujo de trabajo de control de versiones (interactivo)"></iframe>
</div>

<script>
(function () {
  var iframe = document.getElementById('git-flow-iframe');
  if (!iframe) return;

  function resize() {
    try {
      var doc = iframe.contentWindow.document;
      var h = Math.max(doc.documentElement.scrollHeight, doc.body.scrollHeight);
      iframe.style.height = (h + 24) + 'px';
    } catch (e) {}
  }

  iframe.addEventListener('load', function () {
    resize();
    try {
      var ro = new ResizeObserver(resize);
      ro.observe(iframe.contentWindow.document.body);
    } catch (e) {}
    window.addEventListener('resize', resize);
  });
})();
</script>


A continuación te explico paso a paso los elementos que tiene el simulador, cómo puedes usarlos y cuál es el objetivo de cada parte:


## Historia guiada y práctica libre

El simulador tiene dos pestañas:

* **Historia guiada**: te lleva paso a paso por doce situaciones, en orden, con el comando de Git, la explicación de qué hace y el control de RStudio ya listo para que lo uses.
* **Práctica libre**: no sigue un guión. Editas archivos, los preparas, haces commits, simulas cambios en GitHub y pruebas tú mismo qué pasa con push y pull, sin perder nada ni tener un repositorio real detrás.

## Qué significa cada estado

Cada archivo pasa por cuatro estados, los mismos que ves en la leyenda de colores arriba del tablero:

* **Sin rastrear**: es un archivo nuevo que Git todavía no vigila.
* **Modificado**: ya es conocido por Git, pero tiene cambios desde el último commit.
* **Preparado**: marcaste ese cambio con Staged para que entre en el próximo commit.
* **Guardado**: ya quedó guardado en el historial local con un commit.

## Cómo leer el tablero

Esta parte es la misma en las dos pestañas, lo que cambia es quién decide las acciones, tú en práctica libre o la historia guiada paso a paso.

* **En tu computadora**: tiene tres columnas, los tres lugares por los que pasa un archivo antes de quedar guardado, Tu carpeta, Staging y Repositorio.
* **En la nube**: es GitHub, el repositorio remoto.
* **Historial de commits**: dos líneas de tiempo paralelas que avanzan hacia la derecha, una que refleja lo que sucede de forma local en tu computadora y otra en GitHub.

## 12 pasos para aprender

La historia guiada tiene doce pasos. El panel de la derecha simula la pestaña de Git de RStudio, con un botón o una casilla que solo se activa cuando corresponde usarlo, para que relaciones cada acción con su lugar real en RStudio. A lo largo de los doce pasos aparecen las situaciones que más se repiten trabajando con control de versiones:

* Hacer tu primer commit y los siguientes.
* Editar un archivo que ya tenía un commit anterior y volver a prepararlo.
* Que alguien más suba un cambio a GitHub sin que tú lo sepas.
* Resolver un push rechazado haciendo pull primero.

## Más recursos para seguir aprendiendo de forma visual

* [Learn Git Branching (GitHub)](https://github.com/pcottle/learnGitBranching)
* [Visualizing Git](https://github.com/git-school/visualizing-git)
* [git-sim](https://initialcommit.com/tools/git-sim)
* [Git resources for visual learners, GitLab](https://about.gitlab.com/blog/2022/09/14/git-resources-for-visual-learners)
* [Software Carpentry, El Control de Versiones con Git](https://swcarpentry.github.io/git-novice-es/)

Este simulador está disponible bajo licencia [Creative Commons Atribución 4.0 (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.es), la misma que usa Software Carpentry para su material. Puedes usarlo libremente en tus propias clases o talleres, adaptarlo o compartirlo, dando crédito y enlazando a este sitio.

