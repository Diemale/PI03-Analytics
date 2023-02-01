# <h1 align=center><span style="color:blue"> **Análisis de MOOCS** </span></h1>

## **Introducción**
<p>
En este proyecto, nos propusimos  realizar un análisis de datos sobre plataformas de creación de cursos educativos de alcance masivo, conocidos como MOOCS, por sus siglas en inglés. Para iniciarlo contábamos con un puñado de pequeños datasets. El proceso tiene como producto final un dashboard que condensa la información conseguida y que sirve de insumo para una demostración del trabajo realizado.


 El  proyecto consta de cuatro **Jupyter notebooks** que contienen: primero, un scrapper para buscar información adicional sobre los ratings de Udemy. Segundo, un notebook en el que se realizó la primera fase de análisis exploratorio y transformación de datos. Tercero, un archivo con cuatro nubes de palabras para investigar el contenido de los nombres de los cursos. Cuarto, un archivo que contiene tanto  la segunda fase de EDA y ETL como el código que crea nuestro dashboard. 
En todas las etapas mencionadas, utilizamos __Python__ como nuestro lenguaje de programación. Además, utilizamos distintas librerías en las diferentes etapas.

    

<hr>  

## **Desarrollo del proyecto**

### ** Web Scraping**

Debido a que la calidad de los datos distaba de ser la mejor, principalmente porque eran datasets de pocos registros y con datos muy heterogéneos, nos vimos en la necesidad de buscar datos en otras fuentes. La heterogeneidad se debió básicamente a que rara vez encontramos el mismo campo para las tres plataformas, lo que representó un gran desafío.
Por esta razón, utilizando la técnica de Scraping pudimos conseguir datos sobre los ratings de los cursos en Udemy, el código utilizado se encuentra en la primera notebook. Para esta tarea, utilizamos las urls que estaban en los datasets. En cuanto a las librerías, usamos   __BeautifulSoup__ para la conversión de los HTML de las páginas y su posterior procesamiento, también __requests__ para crear las conexiones a las urls. Asimismo, utilizamos una técnica de Scrapping en la segunda notebook. Esta consisitió en conectarse a las url que teníamos de Udemy, notamos que el contenido de las respuestas tenían un valor con patrones diferentes, a veces devolvía el nombre de la url ingresada y otras veces una url diferente con la palabra draft. Al investigar, observamos que las que tenían la palabra clave draft en la url, correspondían a cursos que ya no estaban online. Así que decidimos utilizar esta información en nuestro análislis. En esta ocasión, utilizamos las librerías __httplib2__ 
para realizar las conexiones y __pprint__ para mejorar las visualizaciones de los retornos.

### **Wordcloud**

Para realizar las nubes de palabras con los nombres de los cursos,  utilizamos la libería __WordCloud__, que torna el trabajo muy sencillo. Simplemente tuvimos que proveerle una cadena y lo hicimos creando una serie de __Pandas__  con todos los títulos de los tres dataframes. Convertimos la serie a una lista, luego a una string gigante y pasamos esta string como parámetro al constructor de WordCloud.


### **EDA-ETL**

En el proceso de EDA-ETL tuvimos que homogeneizar un poco los data frames de cada una de las plataformas. Pronto notamos que los datos mostraban dos modelos de negocio diferentes, por lo que decidimos contrastar los datos de Udemy por un lado y los de Coursera junto con Edx, por el otro. Esto además, le dio mucha más flexibilidad al proceso de ingeniería de datos, dado que ya no era imperioso tener una gran cantidad de campos en común para las tres plataformas. En cuanto a lo técnico: en esta etapa realizamos chequeo de datos faltantes, data wrangling, normalizamos tanto los nombres de los campos para que coincidieran con los de los otros data frames, como los valores de los datos de tipo string. Hicimos, además, cambios de tipos de datos, creamos nuevas columnas a través de las existentes, eliminamos valores duplicados, concatenamos data frames, entre otras cosas. En esta etapa, utilizamos Pandas para el tratamiento general de datos, numpy para imputar valores nulos, y seaborn para algunas visualizaciones. 


En la segunda parte del análisis exploratorio y la transformación de datos, nos apoyamos en los gráficos de __hvplots__, que fueron usados en combinación con __Panel__ para la creación de widgets que permitieron controlar los gráficos interactivos. La interactividad la logramos a través de dos métodos. El primero consiste en la creación de un pipeline, que incorpora un data frame interactivo, así como todos los métodos y operaciones realizados sobre este  y por último, un widget para controlar los gráficos. El segundo método utilizado fue el uso de funciones que se encargan de procesar los datos y devuelven un objeto hvplot que  luego es tomado por un widgetbox de Panel. Este a su vez, "envuelve" a la función junto a otro widget y los vincula, de manera tal que el widget vinculado a la función controle la interactividad del gráfico. En algunos de los gráficos utilizamos funciones de agregación gracias a __matplotlib__ y __numpy__.


### **Creación del dashboard**
<p>
Para la creación del Dashboard utilizamos el template bootstrap de Panel, que permite realizar el layout de los gráficos de una manera bastante amena y estética. Este template tiene, básicamente, dos zonas, una sidebar y una zona principal, en la primera pueden disponerse descripciones y widgets controladores de la dinámica de los gráficos. En la segunda se situán los gráficos o widgets contenedores de gráficos. La disposición de esta zona está dada por filas y columnas que se crean desde el código de la persona que realiza el dashboard. Dentro de estas filas y columnas se pueden ubicar los objetos que deseemos. 
</p>



## **Puntos a mejorar en este proyecto**

Los siguientes son algunos puntos que mejorarían el proyecto:

1) Obtener más información a través del scraping de las páginas web para homogeneizar más la data. 

2) Crear un KPI de crecimiento de cursos por mes, en lugar del de crecimiento interanual que creamos

3) A partir de la nueva información crear nuevos gráficos para el dashboard.




## Sitios con información sobre este proyecto

[github del proyecto](https://github.com/Diemale/PI03-Analytics)

[Archivo csv con reviews de Coursera de 252 MB que no puede ser subido a github:](https://drive.google.com/drive/u/1/folders/1f_ehX_AOb8xeWBvADp4XD0Egaarq9XQO)


