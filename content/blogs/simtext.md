---
author: lindateachtech
date: "2023-12-16"
description: ""
draft: false
image: /images/projects/simtext2.jpg
tags:
- Shiny
- SimilitudDelCoseno
- SimilitudTextual
- DataScience
- TextMining
- Rstats
- Automatization
title: ¿Cómo comparar grandes listados de texto de forma precisa?
toc: TRUE
---


> “El lenguaje humano es un sistema de expresión que permite infinitas combinaciones con un conjunto finito de elementos”. </p>
> — <cite>Anónimo</cite>


Imagina que tienes dos extensos listados de productos, nombres o descripciones que necesitas comparar. Hacerlo manualmente sería casi imposible, pero contar con una herramienta que automatice el proceso no solo ahorra tiempo, sino que garantiza resultados más precisos. 

Aquí es donde entra en juego SIMTEXT, una aplicación desarrollada en R con Shiny, ideal para analizar la similitud entre textos de grandes volúmenes.

<br>

## ¿Qué es SIMTEXT y qué puede hacer?

SIMTEXT está diseñada para manejar listados grandes, donde comparar manualmente no es una opción. Sus principales funcionalidades son:

- **Comparación de listados grandes:** Evalúa la similitud entre un listado base y otro listado objetivo.
- **Análisis dentro del mismo listado:** Identifica duplicados o descripciones similares en un único conjunto de datos.
- **Resultados descargables:** Exporta los análisis en formato Excel para compartir o integrar en otros procesos.


<br>

## ¿Qué hace diferente a SIMTEXT?

Que utiliza el cálculo de **similitud del coseno**, un método popular en el análisis de texto. Este algoritmo transforma los textos en vectores y mide el ángulo entre ellos:

- Un índice de 1 indica textos idénticos.
- Un índice de 0 indica que no tienen similitud alguna.

Es ideal para comparar grandes volúmenes de datos textuales, como nombres de productos, reseñas o descripciones.


<br>

## ¿Dónde podría aplicarse SIMTEXT?

Esta herramienta tiene aplicaciones en diversos contextos:

- **Revisión de inventarios:** Detectar duplicados o productos similares en bases de datos extensas.
- **Análisis de descripciones en comercio electrónico:** Identificar discrepancias en nombres o descripciones de productos.
- **Revisión de datos en investigaciones académicas:** Comparar respuestas o textos extensos de encuestas.
- **Control de calidad en contenidos digitales:** Revisar descripciones o etiquetas similares en grandes portales web.
- **Segmentación de datos:** Agrupar textos con alta similitud para análisis más detallados.


<br>

## ¿Cómo funciona técnicamente?

SIMTEXT utiliza una combinación de técnicas avanzadas para garantizar resultados confiables:

- **Preprocesamiento:** Limpia y normaliza los textos eliminando caracteres especiales, espacios adicionales y mayúsculas/minúsculas.
- **TF-IDF:** Una técnica que pondera la importancia de las palabras en un conjunto de textos, mejorando la precisión de los análisis.
- **Similitud del coseno:** Calcula la similitud numérica entre textos basándose en su representación vectorial.


<br>

## ¿Cómo Usar SIMTEXT?

Esta herramienta está diseñada para ser intuitiva y fácil de usar, incluso para aquellos que no tienen experiencia previa con programación. Sigue estos pasos para empezar:

### Paso 1: Subir tus archivos

En la interfaz de usuario, encontrarás dos campos principales para cargar tus archivos:

- **Listado Origen:** Carga aquí el archivo con los textos que deseas analizar. Este archivo debe estar en formato .xlsx.
- **Listado Destino:** Si deseas comparar dos listados distintos, carga aquí el archivo de destino. Si solo tienes un listado y deseas compararlo consigo mismo, selecciona esa opción en el menú desplegable (ver paso 2).


<div>
<p style = 'text-align:center;'>
<img src="/images/simtext/subir_archivos.png" width="950px">
</p>
</div>


### Paso 2: Seleccionar el tipo de análisis

En el menú desplegable, elige el tipo de análisis que deseas realizar:

- **Listado Origen vs. Listado Destino:** Compara textos entre dos archivos distintos.
- **Listado Origen Consigo Mismo:** Compara los textos dentro del mismo archivo de origen.


### Paso 3: Ejecutar la comparación

1. Haz clic en el botón Comparar.
2. La herramienta procesará los textos y calculará la similitud utilizando el método de similitud del coseno.
3. Una tabla de resultados aparecerá en pantalla, mostrando:
    - Los textos originales y sus coincidencias más similares.
    - El índice de similitud correspondiente (valor entre 0 y 1, donde 1 indica una similitud completa).


<div>
<p style = 'text-align:center;'>
<img src="/images/simtext/comparar_listados.png" width="950px">
</p>
</div>


### Paso 4: Descargar los resultados

Una vez finalizado el análisis, puedes descargar los resultados haciendo clic en el botón `Descargar resultados`.

El archivo descargado estará en formato `.xlsx` y contendrá una tabla con todas las comparaciones y sus índices de similitud.



## Consejos para maximizar el uso de la herramienta

- Asegúrate de que los textos estén en un formato limpio antes de subirlos. Esto mejora la precisión del análisis.
- Utiliza archivos grandes para aprovechar al máximo las capacidades de esta herramienta. Si trabajas con listados pequeños, es posible que un análisis manual sea más eficiente.
- Experimenta con diferentes tipos de listados para explorar nuevas aplicaciones, como detección de duplicados o similitudes semánticas.
- La aplicación tomará la primera columna de ambos archivos para realizar la comparación.


**¿Listo para probarla?** [SIMTEXT](https://linda-cabrera.shinyapps.io/simtext/)

La capacidad de comparar listados extensos de texto no solo optimiza el tiempo, sino que también garantiza una mayor precisión y objetividad en los resultados. Herramientas como SIMTEXT demuestran cómo el análisis de texto puede ser más eficiente y accesible para profesionales de diversas áreas.

Si deseas probar esta herramienta, te dejo el enlace para que puedas acceder y explorar su funcionalidad: Probar [SIMTEXT](https://linda-cabrera.shinyapps.io/simtext/) aquí.

¿Te interesa aprender más sobre otras aplicaciones o cómo mejorar tus análisis con R y Shiny? ¡Déjame un comentario o comparte tus ideas! Estaré encantada de saber en qué otros contextos utilizarías esta herramienta y responder a tus preguntas. 🚀


<br>

## Youtube: Tutorial para la instalación paso a paso de R y RStudio

<br>
{{< youtube wM6K81wm2jQ >}}
<br>


