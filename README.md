# lindateachtech — sitio web personal

Sitio web personal de **Linda Cabrera Orellana**, analista de datos, instructora de software y desarrolladora en R.

🔗 **Sitio en vivo:** [lindateachtech.netlify.app](https://lindateachtech.netlify.app/)

## Sobre el sitio

Este repositorio contiene el código fuente de mi portafolio personal, donde comparto mi trayectoria profesional, cursos que he impartido, proyectos de análisis de datos, logros dentro de la comunidad de R y artículos de blog sobre R, ciencia de datos y visualización.

Incluye las siguientes secciones:

- **Resumen** — sobre mí y mi trayectoria profesional.
- **Educación** — formación académica.
- **Blog** — tutoriales y reflexiones sobre R, ciencia de datos y visualización.
- **Cursos impartidos** — cursos y talleres que he dictado.
- **Proyectos** — proyectos de análisis y desarrollo con R.
- **Logros** — reconocimientos y participaciones en la comunidad (rOpenSci, WiDS, R-Ladies, The Carpentries).
- **Contacto** — formulario de contacto y redes sociales.

## Tecnologías

- [Hugo](https://gohugo.io/) — generador de sitios estáticos.
- [blogdown](https://bookdown.org/yihui/blogdown/) — para escribir y construir el sitio desde R/RStudio.
- Tema [hugo-profile](https://github.com/gurusabarish/hugo-profile), personalizado con una identidad visual y paleta de colores propias.
- [Netlify](https://www.netlify.com/) — hosting y despliegue continuo desde este repositorio.
- [Netlify Forms](https://docs.netlify.com/manage/forms/) — para el formulario de contacto.
- [Disqus](https://disqus.com/) — comentarios en las entradas del blog.

## Estructura del proyecto

```
mi_sitioweb/
├── config.yaml           # Configuración general del sitio (Hugo)
├── content/               # Contenido en Markdown (páginas, blog, cursos)
├── layouts/                # Plantillas y componentes propios del sitio
├── static/                 # Imágenes y archivos estáticos
├── themes/hugo-profile/   # Tema base, personalizado directamente en el repositorio
├── netlify.toml            # Configuración de build y despliegue en Netlify
└── mi_sitioweb.Rproj       # Proyecto de RStudio
```

## Cómo ejecutarlo en local

Este sitio se construye con [blogdown](https://bookdown.org/yihui/blogdown/) desde RStudio.

1. Clona el repositorio y ábrelo como proyecto en RStudio (`mi_sitioweb.Rproj`).
2. Instala las dependencias necesarias (paquete `blogdown` y Hugo, si no lo tienes):

   ```r
   install.packages("blogdown")
   blogdown::install_hugo()
   ```

3. Sirve el sitio en local para previsualizar los cambios:

   ```r
   blogdown::serve_site()
   ```

## Despliegue

El sitio se despliega automáticamente en [Netlify](https://www.netlify.com/) con cada `push` a la rama `main` de este repositorio.

## Contacto

- 🔗 [LinkedIn](https://www.linkedin.com/in/lindatech/)
- 🐙 [GitHub](https://github.com/lindateachtech)
- 🐦 [Twitter](https://twitter.com/lindateachtech)
- ✉️ [lindateachtech@gmail.com](mailto:lindateachtech@gmail.com)
