# TP1 - Pandas, Spark y Visualización de datos
## Primera parte - Pandas (8 ptos)

Utilizamos el dump Wikipedia Español [al día 01/09](https://dumps.wikimedia.org/eswiki/20210901/) de 178gb, extrayendo [los siguientes csvs](https://drive.google.com/file/d/1np5j_-9QiYIRPs0GIFDWaT9M2ddvCv-w/view?usp=sharing):
## contents.csv
Tabla con datos de todos los contenidos de Wikipedia en su versión más reciente.

| Campo | Descripcion |
| :- | :- |
|title|Título del contenido|
|id|Identificador único del contenido|
|namespace|🤷|
|revision\_id|Id de la última revisión realizada|
|parent\_revision|Id de la revisión anterior a la actual|
|revision\_timestamp|Timestamp de la última revisión|
|revisor\_username|Username del autor de la última revisión|
|revisor\_id|Id del revisor\_username|
|revisor\_ip|IP del revisor (en caso de que no estuviera registrado)|
|revisor\_comment|Comentario de la revisión|




## contents\_text\_sample.csv

Tiene una muestra aleatoria del 5% de los contenidos de texto de wikipedia

| Campo | Descripcion |
| :- | :- |
|id|Id del contenido|
|title|Título del contenido|
|text|Texto|


## geo\_tags.csv

| Campo | Descripcion |
| :- | :- |
|gt\_id|Id del geo tag|
|gt\_page\_id|Id del contenido al que corresponde|
|gt\_globe|En qué globo se encuentra|
|gt\_primary|🤷|
|gt\_lat|Latitud|
|gt\_lon|Longitud|
|gt\_dim|🤷|
|gt\_type|Tipo de locación|
|gt\_name|Nombre|
|gt\_country|País|
|gt\_region|Región|

## logs.csv

Todo el log de acciones realizadas.

| Campo | Descripcion |
| :- | :- |
|item\_id|ID del item afectado|
|timestamp|Timestamp del log|
|contributor\_username|Username que realizó la acción|
|contributor\_id|ID del user que realizó la acción|
|contributor\_ip|IP (en caso de que no tuviera usuario)|
|comment|Comentario|
|logtype|Tipo de log|
|action|Acción realizada|
|title|Título del log|

## languages.csv

Contiene información sobre qué idiomas habla cada usuario

| Campo | Descripcion |
| :- | :- |
|babel\_user|User id|
|babel\_lang|Código de idioma (ISO 639-2)|
|babel\_level|[Nivel](https://en.wikipedia.org/wiki/Wikipedia:Babel/Levels) en el lenguaje|

## redirect\_list.csv
Algunos de los contenidos de Wikipedia son redirecciones a otros contenidos, esta tabla contiene esa información.

| Campo | Descripcion |
| :- | :- |
|rd\_from|ID del contenido que redirige|
|rd\_namespace|🤷|
|rd\_title|Título del contenido al que redirige|
|rd\_interwiki|🤷|
|rd\_fragment|🤷|

## categorylinks.csv

| Campo | Descripcion |
| :- | :- |
|cl\_from|ID del contenido|
|cl\_to|Categoría a la que pertenece el contenido|
|cl\_sortkey|🤷|
|cl\_timestamp|Timestamp de la asociación de la categoría|
|cl\_sortkey\_prefix|🤷|
|cl\_collation|🤷|
|cl\_type|El tipo de contenido que se asignó a esa categoría|

## pagelinks\_sample.csv
Tabla con links que van de una página interna a otra. Es una muestra de dos tercios.

| Campo | Descripcion |
| :- | :- |
|pl\_from|ID del contenido donde está el link|
|pl\_namespace|🤷|
|pl\_title|Título del contenido al cual va el link|
|pl\_from\_namespace|🤷|


## Pandas
1. La probabilidad de que la versión actual de un contenido fuera editada sin dejar comentario para usuarios que están logueados y que no están logueados (⭐)
2. Para los usuarios nativos (o superior) en español obtenga una serie cuyo índice sea cada uno de los otros idiomas que sabe y valor sea el nivel promedio (tomando N=4.5) (⭐⭐)
3. Obtenga un dataframe que tenga como índice al user\_id, como columnas a los idiomas y el nivel de cada usuario para cada idioma como valor con -1 en caso de no tenerlo cargado. (⭐⭐)
4. Si decimos que la ubicación de una categoría es el promedio de la latitud y longitud de sus contenidos geolocalizados que son miembros de ella (si es que tiene): ¿Cuales son las dos categorías más cercanas? (⭐⭐⭐)

## Segunda parte - Visualización de datos (7 ptos)
1. (3 ptos) Elegir uno de los siguientes datasets:
- [Proyectando el comportamiento de la soja](https://metadata.fundacionsadosky.org.ar/competition/11/)
- [¿Llevo paraguas? Pronosticando la lluvia](https://metadata.fundacionsadosky.org.ar/competition/15/)
- [Predicción de éxitos en oportunidades comerciales](https://metadata.fundacionsadosky.org.ar/competition/20/)
- [Clasificación de preguntas de clientes](https://metadata.fundacionsadosky.org.ar/competition/21/)
- [MELI Data Challenge 2021](https://ml-challenge.mercadolibre.com/downloads)
- [Flu Shot Learning: Predict H1N1 and Seasonal Flu Vaccines](https://www.drivendata.org/competitions/66/flu-shot-learning/page/210/)
- [DengAI: Predicting Disease Spread](https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/page/80/)

Realizar tres visualizaciones que expliquen la variable a predecir conteniendo los siguientes tipos de plots:

- Histograma
- Violin plot o Box plot
- Heatmap

1. (4 ptos) Utilice alguna herramienta para realizar diagramas (por ejemplo Google Draw, draw.io, Google Slides, HTML, Illustrator, Photoshop, etc.) para crear una visualización **ORIGINAL** que no pueda realizarse de forma directa con las librerías más comunes de Python, puede utilizar las librerías de Python como paso intermedio. Puede realizar este punto sobre los datos de: cualquier dataset, estadística oficial, paper, estadística no oficial, encuesta, números sin ninguna fuente en un blog, etc. El objetivo es elegir un tema de su interés y comunicarlo de forma efectiva y agradable.

## Tercera parte: Spark (8 ptos)
## Spark
1. Realizar un análisis de stopwords del contenido de texto de la Wikipedia. En este punto esperamos que analicen, dada la frecuencia de los términos que hay en la wikipedia cuales deberian ser considerados stop words. (⭐)
2. El porcentaje de contenidos que están publicados cuya última edición no tiene comentario para los usuarios que realizaron 1, >10 y >100 de las últimas ediciones  (⭐⭐)
3. ¿Cuál es el mínimo que ha durado desde su registro un usuario bloqueado en la plataforma? (⭐⭐)
4. Si decimos que la ubicación de un usuario es el promedio de la latitud y longitud de los contenidos geolocalizados para los cuales editó la última versión (ignorar usuarios que no editaron contenido geolocalizado). ¿Cuáles son los dos usuarios más cercanos? (⭐⭐⭐)


Criterio de aprobación

El criterio general es que la totalidad del tp tiene que sumar 14 puntos de los 23, un 60%. Pueden hacer consultas por slack.
### **Criterio de reentrega**
Se podrá reentregar el TP si el puntaje es >=10 y están todos los puntos desarrollados. La reentrega consiste en hacer un punto extra y corregir todos los puntos donde tuvieran menos de la mitad de los puntos.

Se aprueba la reentrega si todos los puntos tienen al menos la mitad de los puntos. En caso de aprobar la instancia de reentrega, la nota es siempre 4.
## Primera parte - Pandas
- Todos los ejercicios valen lo mismo que las estrellitas que tienen asignadas, a cada uno le corresponde hacer según indiquemos cual les toca:
  - 1 ejercicio de ⭐
  - 2 ejercicios de ⭐⭐
  - 1 ejercicio de ⭐⭐⭐
- Cada ejercicio se considera 100% correcto si:
  - Resuelve lo pedido (¡cuidado con casos bordes! ¡revisen todo lo que pueda ser NULL!): Si el ejercicio no resuelve al 100% lo pedido, se considera que vale como máximo la mitad
  - Lo hace de la forma más eficiente posible: Si el ejercicio no está resuelto de la forma más óptima, se considera que vale la mitad
- La idea es que no lo hagan solos! Las consignas son complejas de entender en una sola lectura y necesitan pensarse lento, por esto es que es crucial consultar. Para esto hacemos lo siguiente según el tipo de duda:
  - Dudas de consigna:
    - Van a poder consultar en el canal de slack #consultas-tp1-pandas, es MUY importante que antes de consultar vean si su duda no fue resuelta. 
    - En caso de no haber sido resuelta tienen que publicarla siguiendo el formato: “**<NÚMERO DE CONSIGNA>** - La pregunta...”. De esta forma todos podemos buscar fácil si ya se resolvió la duda o sumarnos a la discusión. **No** se debe incluir código de la resolución, ni en la pregunta ni interactuando con otros compañeros.
  - Dudas para saber si se puede usar alguna librería:
    - Se hacen en el mismo formato que las dudas de consigna.
  - Dudas de código y optimización:
    - Si son dudas generales de “cómo se hace algo en pandas” se puede consultar en las clases de consulta o en el canal #otras-consultas
    - El resto de las dudas se deben consultar con algún ayudante por privado.
## Segunda parte - Visualización de datos
1. Cada visualización vale un punto, y debe cumplir con las siguientes condiciones:
   1. Debe explicarse por sí misma, sin necesidad de texto aclaratorio.
   1. Debe tener rótulos en los ejes que corresponda y en el título.
   1. Debe mostrar una relación con el target que sea clara.
   1. El uso del color debe ser intencional, elegido por ustedes, no por la librería.
   1. La visualización debe ser legible (Un bar chart de 40 barras por ejemplo es ilegible)
1. Debe cumplir el objetivo propuesto: Les recomendamos preguntar en clases de consultas o por slack, vamos a estar guiandolos en este punto. Dado que la elección de este dataset es personal, pueden ir compartiendo sus ideas/bocetos o consultando cosas en *#consultas-tp1-visu*.

## Tercera parte: Spark
- Todos los ejercicios deben realizarse utilizando el API de RDD de Spark.
- A cada uno le corresponde hacer según indiquemos cual les toca:
  - 1 ejercicio de ⭐
  - 2 ejercicios de ⭐⭐
  - 1 ejercicio de ⭐⭐⭐
- Cada ejercicio se considera 100% correcto si:
  - Resuelve lo pedido (¡cuidado con casos bordes!): Si el ejercicio no resuelve al 100% lo pedido, se considera que vale como máximo la mitad
  - Lo hace de la forma más eficiente posible: Si el ejercicio no está resuelto de la forma más óptima, se considera que vale la mitad. 
    En este aspecto considerar el buen uso del procesamiento distribuido de spark y potenciales errores que pueda realizar procesando información en el driver.
- La idea es que no lo hagan solos! Las consignas son complejas de entender en una sola lectura y necesitan pensarse lento, por esto es que es crucial consultar. Para esto hacemos lo siguiente según el tipo de duda:
  - Dudas de consigna:
    - Van a poder consultar en el canal de slack #consultas-tp1-spark, es MUY importante que antes de consultar vean si su duda no fue resuelta. 
    - En caso de no haber sido resuelta tienen que publicarla siguiendo el formato: “**<NÚMERO DE CONSIGNA>** - La pregunta...”. De esta forma todos podemos buscar fácil si ya se resolvió la duda o sumarnos a la discusión. **NO SE DEBE incluir código de la resolución, ni en la pregunta ni interactuando con otros compañeros.**
  - Dudas para saber si se puede usar alguna librería:
    - Se hacen en el mismo formato que las dudas de consigna.
  - Dudas de código y optimización:
    - Si son dudas generales de “cómo se hace algo en spark” se puede consultar en las clases de consulta o en el canal #otras-consultas
    - El resto de las dudas se deben consultar por privado
- Todos los ejercicios asignados deben estar resueltos en la entrega.
