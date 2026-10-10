---
author: lindateachtech
date: "2026-10-09"
description: "Herramienta interactiva para enseñar el flujo de trabajo de control de versiones de forma dinámica y que puedan ver en tiempo real cómo va cambiando el estado de cada archivo, en vez de imaginárselo."
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
title: "Simulador de un flujo de trabajo de control de versiones"
toc: TRUE
---


Esta es una herramienta interactiva para enseñar el flujo de trabajo de control de versiones de forma dinámica y que puedan ver en tiempo real cómo va cambiando el estado de cada archivo, en vez de imaginárselo.


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


Este simulador está disponible bajo licencia [Creative Commons Atribución 4.0 (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.es), la misma que usa Software Carpentry para su material. Puedes usarlo libremente en tus propias clases o talleres, adaptarlo o compartirlo, dando crédito y enlazando a este sitio.

