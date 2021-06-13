---
title: Memoria de desarrollo de la PEC3
author: Damián Serrano Thode
date: 11/06/2021
lang: es
geometry: "a4paper,left=2.5cm,right=2.5cm,top=2.5cm,bottom=2.5cm"
mainfont: arev
fontsize: 12pt
linestretch: 1.5
toc_depth: 2
urlcolor: cyan
toccolor: black
linkcolor: black
numbersections: true
header-includes:
   - \usepackage{arev}
---

# Versión inicial de las páginas

## Información de carga

Título|URL|Tiempo de carga|Peso total|Peso transferido|Cantidad de recursos
---|---|---:|---:|---:|---:
Principal|[https://laughing-allen-4aee0b.netlify.app/index.html](https://laughing-allen-4aee0b.netlify.app/index.html)|1.63 s|230.84 KB|175.12 KB|12
Presentación|[https://laughing-allen-4aee0b.netlify.app/presentacion.html](https://laughing-allen-4aee0b.netlify.app/presentacion.html)|24.98 s|6.41 MB|2.17 MB|21
Recetas|[https://laughing-allen-4aee0b.netlify.app/recetas.html](https://laughing-allen-4aee0b.netlify.app/recetas.html)|2.64 s|334.99 KB|279.05 KB|15
Enlaces|[https://laughing-allen-4aee0b.netlify.app/enlaces.html](https://laughing-allen-4aee0b.netlify.app/enlaces.html)|1.63 s|186.57 KB|124.33 KB|11
Cheese Burger|[https://laughing-allen-4aee0b.netlify.app/cheese-burger.html](https://laughing-allen-4aee0b.netlify.app/cheese-burger.html)|3.83s|352.5 KB|291.81 KB|15
Costillas|[https://laughing-allen-4aee0b.netlify.app/costillas.html](https://laughing-allen-4aee0b.netlify.app/costillas.html)|3.81 s|406.62 KB|340.25 KB|16
Brownie|[https://laughing-allen-4aee0b.netlify.app/brownie.html](https://laughing-allen-4aee0b.netlify.app/brownie.html)|3.15 s|338.48 KB|272.39 KB|16

Los tiempos de carga de las páginas son razonables para una conexión configurada a velocidad 3G, sin embargo, la página de Presentación tiene un tiempo de carga tan elevado por la presencia de los vídeos empotrados desde Youtube. Estos vídeos se cargan mediante un iframe, que causan una gran cantidad de datos transferidos para personalizar la presentación de los mismos.

# Primera iteración de Page Speed Insights

https://blissful-elion-6a5980.netlify.app/presentacion.html

Vistos los resultados de Page Speed Insights, la primera cosa que llevé a cabo fue asignar el tamaño a las imágenes de las páginas, puesto que no les había asignado estos atributos ya que estaba usando el modo de *responsive images*,en el cual ya no se indicaban estos atributos. Según he podido leer en la documentación disponible en internet, los navegadores usan ahora estos atributos para estimar la relación de aspecto de las imagenes y poder estimar el espacio que ocuparán en la página, para así evitar el efecto de *Cumulative Layout Switch*.

Otra de las acciones llevadas a cabo fue asignar el atributo *loading="lazy"* a las imágenes e iframes de vídeos cargados desde Youtube para reducir el efecto en el tiempo de carga de la página. En este aspecto sí espero una mejora en los resultados de carga de la página de presentación, ya que al cargar tres vídeos de Youtube tiene una puntuación muy baja en Page Speed Insights por la sobrecarga que impone el pocesamiento del *iframe*.

Tras comprobar los tiempos de carga, reflejados en la tabla del punto siguiente, observo que no ha habido una mejora en los tiempos de carga de la página de Presentación usando Mozilla Firefox, y tras consultar la documentación de [Can I Use](https://caniuse.com/loading-lazy-attr) sobre el atributo "loading", observé que el soporte del mismo en Firefox esta limitado únicamente a las imágenes, por lo que para la elaboración de los datos de carga de dicha página usé el navegador Chrome.

Analizando la tabla de información de carga, se puede observar una considerable mejora en los tiempos de la página de Presentación, únicamente disponible en el navegador Google Chrome, eso sí, por lo que la repercusión final de dicho cambio es limitada.

En cuanto al resto de las páginas, los tiempos sí tienen una ligera mejora, la cual debe ser atribuible al uso del atributo loading en las imagenes de la página.

## Información de carga

Título|URL|Tiempo de carga|Peso total|Peso transferido|Cantidad de recursos
---|---|---:|---:|---:|---:
Principal|[https://blissful-elion-6a5980.netlify.app/index.html](https://blissful-elion-6a5980.netlify.app/index.html)|1.66 s|230.18 KB|174.92 KB|13
Presentación|[https://blissful-elion-6a5980.netlify.app/presentacion.html](https://blissful-elion-6a5980.netlify.app/presentacion.html)|19.47 s|7.7 MB|2.5 MB|48
Recetas|[https://blissful-elion-6a5980.netlify.app/recetas.html](https://blissful-elion-6a5980.netlify.app/recetas.html)|2.74 s|335.26 KB|268.84 KB|15
Enlaces|[https://blissful-elion-6a5980.netlify.app/enlaces.html](https://blissful-elion-6a5980.netlify.app/enlaces.html)|1.69 s|192.73 KB|125.90 KB|11
Cheesburger|[https://blissful-elion-6a5980.netlify.app/cheese-burger.html](https://blissful-elion-6a5980.netlify.app/cheese-burger.html)|2.47 s|304.03 KB|237.25 KB|13
Costillas|[https://blissful-elion-6a5980.netlify.app/costillas.html](https://blissful-elion-6a5980.netlify.app/costillas.html)|2.44 s|352.82 KB|286.10 KB|13
Brownie|[https://blissful-elion-6a5980.netlify.app/brownie.html](https://blissful-elion-6a5980.netlify.app/brownie.html)|2.69 s|303.81 KB|236.99 KB|13


# Segunda iteración de Page Speed Insights

Para la segunda iteración de la página he intentado abordar las recomendaciones que quedaban pendientes en Page Speed Insights, que eran la eliminación del CSS superfluo, usando varios plugins disponibles para esta tarea, y la de eliminar los recursos que bloquean el renderizado eliminando la referencia a Google Fonts para la fuente personalizada que se usa en el sitio web.

Sin embargo, esta tarea de eliminar las fuentes de Google Fonts no la he llevado a cabo ya que el uso de esta fuente es un elemento importante del diseño de la misma, y no estaría justificado el eliminarla de la página y alterar su diseño.

La eliminiación del CSS superfluo es importante, ya que estoy usando las fuentes de iconos de FontAwesome y estas incluyen una gran cantidad de clases CSS para todos los posibles iconos que se pueden utilizar, sin embargo, en esta página estoy usando únicamente dos o tres de estos iconos, por lo que cargar un archivo CSS de aproximadamente 60 KB para usar únicamente unas pocas decenas de bytes es un gasto inútil.

Por lo tanto, para eliminar el CSS superfluo, en primer lugar he intentado usar el plugin de parcel [parcel-plugin-purgecss](https://www.npmjs.com/package/parcel-plugin-purgecss), sin embargo ha sido imposible conseguir que funcionara, ya que de todas las formas en que lo he probado siempre me generaba el CSS de Fontawesome completo.

En segundo lugar he probado el plugin [PostCSS-PurgeCSS](https://www.npmjs.com/package/@fullhuman/postcss-purgecss), sin embargo este plugin requiere la versión 8 de PostCSS y Parcel v1 incluye una versión anterior y no es compatible con ésta.

Y en tercer lugar he probado el plugin [PostCSS-UnCSS](https://www.npmjs.com/package/postcss-uncss), sin embargo al probarlo ha dado errores al procesar los archivos Javascript, algo que no entiendo ya que se trata de procesar el contenido CSS. Al buscar documentación sobre el problema no he encontrado nada que me sirva de ayuda ya que además la versión 1 de Parcel ya está obsoleta y todas las referencias encontradas son siempre a la versión 2 de Parcel.

Por lo tanto, para la segunda fase he sufrido lo que se conoce como agotamiento del frontend, que consiste en que las tecnologías usadas en la construcción de páginas web en el lado de frontend cambian a una velocidad inusualmente alta y proyectos que tienen uno o dos años son abandonados por otros recién creados y esto causa un agotamiento en los desarrolladores de frontend al tener que estar continuamente cambiando la estructura de los proyectos de frontend.

# Anexos

En la carpeta de anexos se incluyen los informes de Page Speed Insights de la versión inicial y de la primera iteración, ya que no he podido llevar a cabo las modificaciones que quedaban para la segunda iteración por imposibilidad técnica.