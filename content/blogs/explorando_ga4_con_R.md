---
author: lindateachtech
date: "2024-01-06"
description: ""
draft: false
image: /images/ga4_r/blog5_portada.jpg
tags:
- API
- GoogleCloud
- GoogleAnalytics4
- DataScience
- RStudio
- Rstats
title: "Explorando Google Analytics 4 con R: Descarga y Análisis de Datos Simplificado"
toc: TRUE
---


¿Sabías que con R puedes extraer tus datos de Google Analytics 4 (GA4) para realizar análisis personalizados y diseñar dashboards únicos? 🚀 ¿O que puedes automatizar el acceso a métricas clave de tu sitio web para integrarlas con otras herramientas?

GA4 es una herramienta esencial en el marketing digital, diseñada para proporcionar una visión integral del comportamiento de los usuarios en sitios web y aplicaciones. Sin embargo, aunque su interfaz ofrece potentes visualizaciones, extraer los datos directamente desde la plataforma brinda ventajas significativas. Al hacerlo, puedes personalizar los análisis según tus necesidades específicas, combinar datos con otras fuentes externas y construir dashboards más avanzados en herramientas especializadas, lo que te da un control total sobre las métricas.

En mi experiencia, esta capacidad me ha sido de gran ayuda para llevar los datos al siguiente nivel. He utilizado los datos extraídos para realizar predicciones de métricas clave, identificar tasas de conversión y correlaciones entre variables, lo que me permite anticipar tendencias y tomar decisiones informadas. Además, los he integrado con herramientas de visualización como Power BI, Looker y Looker Studio, creando dashboards interactivos y fáciles de interpretar. 

Aquí es donde R entra en acción para facilitarte el trabajo. ¿Listo para descubrir cómo? 🖥️ 

En este tutorial, te guiaré paso a paso para conectar GA4 con R y descargar datos clave que podrás analizar según tus necesidades. 🖥️

<br>

## ¿Qué necesitarás?

- Una cuenta de Google Cloud con acceso a la API de GA4.
- Permisos de administrador para el proyecto de GA4 que deseas analizar.
- R y RStudio instalados en tu equipo.

Si no sabes lo que es una API de Google Cloud y cómo obtenerla, aquí te enseñaré paso a paso.

<br>

## Configuración Inicial

### Paso 1: Activa la API de Google Analytics Data API

Empezamos creando un proyecto en Google Cloud y activando la API de GA4. Una API es una interfaz de programación de aplicaciones que permite a los desarrolladores extraer datos, automatizar tareas, integrar servicios en este caso de Google Cloud en aplicaciones propias y aprovechar funcionalidades avanzadas sin necesidad de gestionar manualmente la infraestructura subyacente.

- Ve a Google Cloud Console de la cuenta de gmail donde tienes activado el servicio de GA4.
- En el menú de navegación elige la opción “API y servicios”, luego elige la opción “APIs y servicios habilitados” y habilita la API “Google Analytics Data API”.

<div>
<p style = 'text-align:center;'>
<img src="/images/ga4_r/GAdataAPI.jpg" width="750px">
</p>
</div>

- El siguiente paso es crear la clave API, para esto debes tener configurada la pantalla de consentimiento de OAuth en el ordenador que estás trabajando.
- Luego, crea el ID de clientes OAuth 2.0 y descarga el archivo JSON correspondiente que deberás guardar en un lugar seguro de tu ordenador.

<div>
<p style = 'text-align:center;'>
<img src="/images/ga4_r/archivoJSON.jpg" width="750px">
</p>
</div>

<br>

### Paso 2: Instala y carga las librerías en R

- Instala y carga en este mismo orden las librerías `googleAuthR` y `googleAnalyticsR`.
- `googleAuthR` es una base para manejar la autenticación OAuth 2.0 en las API de Google y básicamente se utiliza para obtener acceso seguro a los servicios de Google. 
- `googleAnalyticsR` está construido sobre googleAuthR y permite extraer datos de Google Analytics y GA4 mediante sus APIs.

``` r
library(googleAuthR)
library(googleAnalyticsR)
```

<br>

### Paso 3: Autentícate en tu cuenta de Google

Carga el archivo `JSON` con tus credenciales que generaste en Google Cloud Console.

``` r
gar_auth_service(json_file = "ruta_a_tu_archivo.json")
```

<br>

## Programa la extracción de datos con R

### Paso 4: Conexión con GA4

Para conectar con tu propiedad de GA4, necesitas su ID. Puedes encontrarlo en la configuración de tu cuenta de Google Analytics con la función `ga_accounts()`.

<br>

### Paso 5: Descarga de datos

Puedes extraer métricas clave de GA4 como visitas, usuarios y conversiones en un rango de fechas específico con la función `ga_data()`.

``` r
trafico_2024 <- ga_data(0000000005,
                        metrics = c("sessions", "ecommercePurchases", "totalrevenue"),
                        dimensions = c("date", "country", "sessionDefaultChannelGroup"),
                        date_range = c("2024-01-01", "2024-12-31"),
                        limit = -1)
```


Puedes encontrar un catálogo de todas las dimensiones y métricas disponibles para una propiedad en [https://ga-dev-tools.google/ga4/dimensions-metrics-explorer/](https://ga-dev-tools.google/ga4/dimensions-metrics-explorer/).

<br>

### Paso 6: Exploración y Análisis

Con los datos descargados, puedes empezar a analizar patrones clave. Por ejemplo, visualización del tráfico por canal:

``` r
trafico_2024 %>%
    group_by(date, sessionDefaultChannelGroup) %>%
    summarise(sessions = sum(sessions)) %>%
    ggplot(aes(x=date, y = sessions, color = sessionDefaultChannelGroup)) +
    geom_line() +
    labs(title = "Evolución de Tráfico Web por Canal",
         x = " ",
         y = "Sesiones",
         color = "Canal") + 
    theme_minimal()
```

<div>
<p style = 'text-align:center;'>
<img src="/images/ga4_r/grafico1.jpg" width="950px">
</p>
</div>


Conectar GA4 con R nos brinda la capacidad de acceder directamente a nuestros datos y trabajar con ellos de manera completamente personalizada. Este enfoque no solo facilita la integración con otras herramientas de inteligencia de negocio, sino que también abre un mundo de posibilidades para analizar y visualizar métricas clave del negocio. 🎯

En otro artículo te mostraré cómo conectar estos datos con Power BI para mantener un dashboard de métricas de tu sitio web actualizado automáticamente. Además, exploraremos otros análisis que puedes realizar para sacar el máximo provecho a estos datos, desde predicciones hasta segmentaciones avanzadas. 🚀

¿Qué opinas? ¿Tienes dudas o curiosidad por algún tema en particular? ¡Déjamelo en los comentarios y sigamos aprendiendo juntos! 😊

<br>


