<h1 align='center'>
 <b>PROYECTO INDIVIDUAL Nº2</b>
</h1>
 
# <h1 align="center">**`Accidentes aéreos`**</h1>

<p align="center">
<img src="https://slack-imgs.com/?c=1&o1=ro&url=https%3A%2F%2Fcdn.pixabay.com%2Fphoto%2F2016%2F09%2F15%2F16%2F13%2Fairplane-1671967_1280.jpg"  height=300>
</p>

## **Desarrollado por Jesús Arteaga Vela**
<hr>

## **Contexto**

Los accidentes aéreos son sucesos imprevistos e impactantes, ya que contradicen las expectativas asociadas al considerarse el medio de transporte más seguro del mundo. Sin embargo, su ocurrencia puede atribuirse a diversos factores, como errores humanos, fallos en los equipos, condiciones meteorológicas desfavorables, problemas de mantenimiento, deficiencias en la gestión del tráfico aéreo, fallos de diseño o inconvenientes en la fabricación. Estas circunstancias pueden resultar en pérdidas humanas y económicas significativas.

Es por eso que la industria de la aviación, en conjunto con las autoridades reguladoras y los investigadores, trabajan incansablemente para mejorar la seguridad aérea y prevenir futuros accidentes.

En este sentido, el análisis de datos históricos de accidentes aéreos desempeña un papel fundamental en la mejora de la seguridad de la aviación. La recopilación y el análisis sistemático de estos datos permiten a los investigadores identificar patrones, tendencias y factores contribuyentes que podrían impulsar mejoras en la seguridad. Esto abarca desde la mejora de la capacitación de los pilotos y el personal de mantenimiento, hasta el perfeccionamiento del diseño y la fabricación de aeronaves y equipos de aviación.

<hr>

## **Rol a desarrollar**

La **Organización de Aviación Civil Internacional (OACI)**, ha decidido llevar a cabo un proyecto de data analytics para analizar los accidentes aéreos de aviones en todo el mundo.


El propósito de este proyecto consiste en reunir, examinar y representar de manera visual datos pertinentes sobre incidentes aéreos con el fin de detectar pautas y tendencias relacionadas con la seguridad de la aviación civil. La ejecución de este proyecto se basará en la aplicación de técnicas de análisis de datos, con el objetivo de procesar y analizar la información recopilada de accidentes aéreos.

Para llevar a cabo el proyecto, la Organización de Aviación Civil Internacional (OACI) proporciona los datos de accidentes de aviones,[AcidentesAviones.csv](https://github.com/jarteaga97/PI02_Analytics_Arteaga/tree/main/datasets).

El resultado final del proyecto es un panel de control interactivo, [PI_Analytic2.pbix](https://github.com/jarteaga97/PI02_Analytics_Arteaga/blob/main/PI_Analytic2.pbix), este permite tener información sobre accidentes específicos. Este panel de control será utilizado para presentar los hallazgos derivados del análisis de la información.

![Imagen presentacion](pictures/imagen0.png)

Así mismo en este trabajo, se visualizará en el panel de control los siguiente indicadores claves de rendimiento (KPI), con el objetivo de comprender los datos y alinearse con los objetivos de la organización:

+ Reducir en 5% la tasa de mortalidad a nivel anual, siendo la tasa el número de fallecidos en los accidentes aéreos sobre el total de personas a bordo en los vuelos involucrados.

$$ d = (D/T)*1000$$

donde:

d : Tasa Bruta de Mortalidad <br>
D : Cantidad de defunciones ocurridas en el año <br>
T : Cantidad de personas que participaron a bordo de los vuelos<br>

La tasa multiplicada por mil, representa la frecuencia relativa con la que ocurren las defunciones en una población durante un año.

+ Aumentar en 10% la tasa de supervivencia a nivel anual, siendo la tasa el número de supervivencia en los accidentes aéreos sobre el total de personas a bordo en los vuelos involucrados.

$$ s = (S/T)*1000$$

donde:

s : Tasa Bruta de Supervivencia <br>
S : Cantidad de sobrevivientes ocurridas en el año <br>
T : Cantidad de personas que participaron a bordo de los vuelos<br>

La tasa multiplicada por mil, representa la frecuencia relativa con la que se salvan las personas en una población durante un año.

<hr>

## **Propuesta de trabajo**

#### `Proceso de "ETL"` _(Extract, transform, load)_ en VisualStudioCode - Python:

+ Importar librerías y dataset.
+ Eliminar la columna 'Unnamed: 0', no aporta información relevante.
+ Pasar a formato minusculas todas las columnas.
+ Renombrar las columnas, previo al análisis.
+ Observar nulos y duplicados
+ Adecuar al formato de 24 horas la columna 'hora_declarada'
+ Eliminar las columnas 'numero_de_vuelo','registro','serie_o_fuselaje','resumen'.
+ Eliminar las coolumnas 'pasajeros','tripulacion', 'pasajeros_fallecidos','tripulacion_fallecida', previo análisis.

#### `Análisis Exploratorio de los datos` (_Exploratory Data Analysis = EDA_)

+ Explorar la frecuencia de los datos de las columnas 'lugar_impacto', 'operador', 'ruta'
+ Crear una columna 'anio', para el análisis de incidencia de accidentes anuales.
+ Graficar total de accidentes por año.
![Dashboard tasa de mortalidad](pictures/EDA1.png)

+ Graficar total de fallecidos por año.
![Dashboard tasa de mortalidad](pictures/EDA2.png)

+ Crear la columna 'supervivientes', como diferencia entre personas a bordo menos las personas fallecidas.
+ Grafica de personas fallecidas vs las supervivientes.
![Dashboard tasa de mortalidad](pictures/EDA3.png)

+ Graficar total de personas fallecidas por modelo de aeronave.
![Dashboard tasa de mortalidad](pictures/EDA4.png)

+ Guardar el nuevo dataset con las transformaciones.

#### *Nota: La extracción de datos así como las respectivas transformaciones pueden verse desarrolladas en el archivo ([ETL-EDA.ipynb](https://github.com/jarteaga97/PI02_Analytics_Arteaga/blob/main/ETL-EDA.ipynb))*
<hr>

#### `Dashboard` en Power BI

+ Desarrollo del primer KPI, `Tasa de mortalidad`, con el objetivo de reducir en un 5% la tasa de mortalidad de manera anual.

Para el primer objetivo, presento distintas visualizaciones que nos brindan información sobre el comportamiento de las personas a bordo, las fallecidas y su variación porcentual año a año.

![Dashboard tasa de mortalidad](pictures/imagen1.png)

Gráficas de líneas, tarjetas, gráfica de columnas apiladas, con una segmentación dispuesta por rango, el cual muestra el comportamiento de la variación porcentual de la tasa de mortalidad en un determinado periodo de tiempo.

Medidor con alarma, el cual posee una métrica que indica cuando se está cumpliendo el objetivo y cuando los valores de variación porcentual son malos, con una escala de colores de verde, amarillo y rojo.
<hr>

+ Desarrollo del segundo KPI, `Tasa de supervivencia`, con el objetivo de aumentar en un 10% la tasa de supervivencia anual.

![Dashboard tasa de mortalidad](pictures/imagen2.png)

Para este segundo objetivo, presento métricas que ayudan visualmente a comprender el comportamiento de las personas que se salvaron comparadas con las que estuvieron a bordo, además de tarjetas, gráfico de pastel, una tabla que se modifica por segmentacion en un rango temporal y brinda un top 10 de sobreviviemtes por modelo de aeronave y el porcentaje que esto representa en comparación con todas las personas a bordo, además de un termómetro que se modifican por segmentación mosaica para observar la variación porcentual de supervivientes por año.

+ Desarrollo del segundo KPI, `Tasa de accidentabilidad`, con el objetivo de aumentar en un 10% la tasa de supervivencia anual.

<hr>

![Dashboard tasa de mortalidad](pictures/imagen3.png)

Para este tercer objetivo, presento métricas en forma de mapa para que ayude a ubicarnos en cuanto al lugar de impacto y que tan frecuente puede ser espacialmente un accidente aéreo, asímismo la tarjeta de Total de accidentes para mostrar un métrica concisa y muy importante, además de gráfica de barras el cual nos muestra un paneo general de toda la accidentabilidad de los vuelos aéreos, el termómetro con el objetivo marcado, segmentación mosaica y por rango el cual nos permite navegar a lo largo de los años y observar su comportamiento.

#### *Nota: El dinamismo del dashboard puede verse en ([PI_Analytic2.pbix](https://github.com/jarteaga97/PI02_Analytics_Arteaga/blob/main/PI_Analytic2.pbix))*
<hr>

### *Así mismo este informe lo puedes observar en linea con el siguiente link ([PI_Analytic2](https://app.powerbi.com/view?r=eyJrIjoiNzA1MzFlYmItNDEwZS00ZWRmLTk4NTYtYmQ4Njk0MGYwZjQ1IiwidCI6IjFlYmE0NDNmLTIzZTUtNDUzNC05MGQxLTA5NzZhYWJlODZhYyIsImMiOjR9))*
<hr>