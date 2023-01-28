![HenryLogo](https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png)
​
# Proyecto individual 2 - Machien Learning Aplicado en el Mercado inmobiliario

Hola soy [Roy Quillca](https://www.linkedin.com/in/royquillca/) este es el segundo Proyecto Individual del Bootcamp de Data Science de Soy Henry. El desarrollo del proyecto ha implicado poner en prática mis habilidades en el campo de la predicción de datos. Especificamente se ha desarrollado el problema de Clusterización de ventas de inmuebles. Para medir la performance del modelo se ha tenido en cuenta la métrica del coeficiente de Silueta cierta métrica.

​
## Description del problema
​
Dentro de la sociedad globalizada e industrializada, es sabido que los precios de los inmuebles han presentado un constante cambio, por lo que quienes deseen invertir o vender una propiedad se enfrentan al fenómeno especulativo existente en la valorización de éstos. Esto, debido a la constante tendencia de las ciudades a crecer demográfica y comercialmente, llegando a un punto en donde no se tiene certeza de la valorización real dentro del sector en donde se desee invertir. 
​
Pese a que el precio depende, en cierta medida, de las tendencias que esté teniendo el mercado inmobiliario en un determinado tiempo, poder estimar adecuadamente el valor de una propiedad es una referencia clave para entender si es una buena oportunidad, ya sea de compra o de venta.
​
## Mercado inmobiliario
​
Usted ha sido contactado para el área de Machine Learning de una importante empresa inversora dentro del rubro de la inmobiliaria en Estados Unidos. 
​
El Team Lider le propone dos predicciones posibles, de las cuales puede elegir cuál realizar (o ambas si así lo quiere):
​
1. Implementar un modelo de clasificación con aprendizaje supervisado que permita clasificar el precio de las propiedades en venta, utilizando los datos que se han puesto a su disposición.
​
Para esto debe crear la columna `category_price`, en la cual se consideran las categorías
   * 'low': Para precios entre 0 y 999 dólares.
   * 'medium': Para precios entre 1000 y 1999 dólares.
   * 'high': Para precios desde 2000 dólares en adelante. 
​
    Considerando esta categorización, el objetivo es predecir si una propiedad pertenece a la categoría de precios bajos (low).
​
2. Implementar un modelo de clasificación con aprendizaje no supervisado, utilizando clustering que agrupe las propiedades por segun las **3 categorias** a las que pueden pertenecer. Para ello, solo usaran el dataset de test provisto, eliminando previamente las caracteristicas que presenten nulos.

El desarrollo del presente proyecto resuelve el segundo la segunda consigna que se trata de implementar el modelo basado en aprendizaje no supervisado.
​​
## Métrica a utilizar
​
Como método de evaluación del desempeño, dependerá del modelo que usted decida implementar.
​
1. Para el modelo de aprendizaje supervisado, se utilizará la métrica `Accuracy` para las propiedades de precio bajo (low) a partir de la matriz de confusión (Confusion Matrix).

$$ Accuracy=\frac{TP+TN}{P+N}$$

siendo $TP$ los verdaderos positivos (las propiedades de precio 'low' que realmente lo son), $TN$ verdaderos negativos (las propiedades que realmente NO son de precio 'low') y $P+N$ población total.

Como métrica adicional para verificar el desempeño de su modelo, también se utilizará la métrica de precisión (Recall) para las propiedades baratas.

$$ Recall=\frac{TP}{TP+FN}$$

​
Donde $TP$ son los verdaderos positivos (las propiedades de precio 'low' que realmente lo son) y $FN$ los falsos negativos (las propiedades de precio 'low' que fueron marcadas incorrectamente).

​
2. Para el modelo de aprendizaje no supervisado, se utilizará la métrica `Silhouette score`.

$$ Silhouette=\frac{b_i-a_i}{max(b_i,a_i)}$$

Dónde $b_i$ es la distancia promedio al grupo más cercano desde el punto i, $a_i$ es la distancia promedio a todos los demás puntos del clúster al que pertenece el punto i. 
​
## **Criterio de evaluación**

Deberán crear un repositorio en GitHub con acceso público donde subirán la solución propuesta en un archivo de Jupyter Notebook (.ipynb) o bien un script de Python (.py) y el archivo de texto plano con valores separados por comas (.csv) con las predicciones. Dicho repositorio deben compartirlo en el formulario de entrega, junto al archivo .csv con las predicciones. Deberán escribir su propio readme, describiendo brevemente el problema y la solución que proponen (no debe ser una simple copia de la consigna del PI).

La solución propuesta debe incluir además los siguientes ítems, por cada uno cumplido sumará 1 punto, siendo 1 la nota mínima y 5 la nota máxima:

- Entrenamiento y predicción utilizando un Modelo de Machine Learning adecuado al problema (clasificación o regresión), o no supervisado en caso de elegir esa vía.
- Análisis exploratorio de los datos (EDA).
- Repositorio de GitHub propio, con un readme redactado introduciendo su proyecto (no debe ser simplemente copia del que le presentamos)
- Comentarios y redacción con la fundamentación de la solución propuesta, escrita en Markdown en el Jupyter Notebook (.ipynb) o bien en un documento aparte.
- Entregar ambos modelos, uno supervisado y otro no supervisado.

Recomendaciones:
- División de dataset en train y test utilizando train_test_split, CV, KFold o similares.
- Utilización de Pipelines en la producción del modelo.

## Archivos provistos
​
Se proveen los siguientes archivos en formato parquet:
 - 'train.parquet': Contiene 346479 registros y 22 dimensiones, el cual incluye la información **numérica** del precio en la columna `price`.
 - 'test.csv': Contiene 38498 registros y 21 dimensiones, el cual no incluye la información del precio. 

 Link al dataset: https://drive.google.com/drive/folders/1nJ9ZMj6E6zh6McC9NwCA6KopfUIOG_1O
​
## Descripción de las dimensiones
- id: Identificador del anuncio. 
- url: Link web del anuncio.
- region: Región de Estados Unidos en donde se encuentra la propiedad.
- region_url: Link web de los anuncios pertenecientes a la región. 
- price: Precio de la propiedad en dólares.
- type: Tipo de propiedad.
- sqfeet: Metros cuadrados de la propiedad.
- beds: Cantidad de dormitorios.
- baths: Cantidad de baños.
- cats_allowed: Si se permiten gatos en la propiedad toma el valor 1, 0 para caso contrario.
- dogs_allowed: Si se permiten perros en la propiedad toma el valor 1, 0 para caso contrario.
- smoking_allowed: Si se permite fumar en la propiedad toma el valor 1, 0 para caso contrario.
- wheelchair_access: Si la propiedad posee acceso para sillas de ruedas toma el valor 1, 0 para caso contrario.
- electric_vehicle_charge: Si la propiedad posee cargador para vehículos eléctricos toma el valor 1, 0 para caso contrario.
- comes_furnished: Si la propiedad viene amueblada toma el valor 1, 0 para caso contrario.
- laundry_options: Opciones de lavandería (w/d in unit: Lavadora/secadora en la propiedad, w/d hookups: conexión para lavadora/secadora, laundry on site: servicio de lavandería en el lugar, laundry in bldg: servicio de lavandería en el edificio, no laundry on sit: sin servicio de lavandería).
- parking_options: Opciones de estacionamiento (off-street parking: zona de estacionamiento, attached garage: garaje incluido, carport: cochera/garaje abierto, detached garage: garaje separado, street parking: estacionamiento delimitado en la calle, no parking: sin estacionamiento, valet parking: estacionamiento con servicio valet).
- image_url: Link web de la imagen de la propiedad en el anuncio. 
- description: Descripción de la propiedad puesta en el anuncio. 
- lat: Latitud.
- long: Longitud.
- state: Código del estado al que pertenece la propiedad.
​
## Sugerencias
- Exploren el dataset. Saquen medidas resumen, vean distribuciones de los datos, analicen bien el tipo de problema, etc.
- Piensen que tipo de modelo podría ser aplicable según la descripción del problema y el tipo de variable de salida.
- Busquen información sobre la métrica aplicada, cada métrica tiene pros y contras.
- Siempre que vean en un dataset coordenadas geoespaciales, es buena estrategia revisar que las mismas correspondan en el mapa al lugar que deberían.
- Si se presentan comentarios, es una buena oportunidad de aplicar procesamiento del lenguaje natural (NLP) para mejorar nuestro modelo.
- En cuanto a la utilización de git, recuerden que si quieren hacer un cambio experimental pero no quieren romper el modelo, pueden utilizar [branching](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging).
- Aprovechen esta instancia de aprendizaje, experimenten y, sobre todo, ¡diviértanse!

## Disclaimer  
De parte del equipo de Henry se quiere aclarar y remarcar que los fines de los proyectos propuestos son exclusivamente pedagógicos, con el objetivo de realizar proyectos que simulen un entorno laboral, en el cual se trabajen diversas temáticas ajustadas a la realidad.
 No reflejan necesariamente la filosofía y valores de la organización. Además, Henry no alienta ni tampoco recomienda a los alumnos y/o cualquier persona leyendo los repositorios (y entregas de proyectos) que tomen acciones en base a los datos que pudieran o no haber recabado. Toda la información expuesta y resultados obtenidos en los proyectos, nunca deben ser tomados en cuenta para la toma real de decisiones (especialmente en la temática de finanzas, salud, política, etc.).
