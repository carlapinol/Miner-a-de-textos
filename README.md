# Clasificación de textos mediante combinación de clasificadores

La clasificación de textos es un proceso mediante el cual se asigna una categoría específica a un texto determinado entre varias opciones disponibles. Este proceso es fundamental en el análisis de datos textuales y tiene numerosas aplicaciones prácticas.

En esta práctica se va a aplicar a reviews de Tripadvisor, clasificándolas en positivas, neutrales o negativas, es decir, vamos a realizar análisis de sentimientos. Para ello vamos a combinar varios clasificadores, cada uno de ellos hace sus predicciones. Estas se combinan y conforman la entrada del esemble junto al texto inicial que se les proporciona a cada uno de ellos, obteniendo así la predicción final.

Los modelos van a ser los siguientes:

* Modelo 01: Pipeline para clasificación de textos
  El primer modelo será un pipeline básico para la clasificación de textos, vamos a tener en cuenta stop words, y las listas de palabras tanto positivas como negativas.
  Utiliza un clasificador SVC.
  
* Modelos 02: Customizado
  Se diseñan las capas del transformer, determinando el número de preclassifiers, dropouts y classifores.
  Vamos a considerar en nuestro modelo customizado el input de los textos a clasificar y una bolsa de palabras positivas para reforzar el sentimiento positivo. Luego probaremos introduciendo también palabras negativas y veremos si conseguimos mejores resultados.
  Además, podemos incorporar estas listas de palabras en distintos puntos del transformer y tener estructuras diferentes, vamos a ver tres formas distintas (al inicio y tras un primer classifier)  y elegiremos el que mejor resultados obtenga.

* Modelo 03: Fine-tunned Transformer (DistilBERT)
  El tercer y último clasificador será un modelo basado en Transformers, entrenado específicamente en nuestros datos. En este caso, es necesario tokenizar y convertir a tensores los datos de acuerdo con los requisitos de Transformers.
  En los inputs del modelo añadimos las listas de palabras positivas y negativas junto a los textos para que este modelo también las tenga en cuenta.

Una vez entrenados y probados los tres modelos se combinan las salidas de los modelos base para construir el ensemble. Además de las predicciones, también se puede tener en cuenta el texto de las reviews y ver cómo afecta a la predicción

Cabe destacar que lo primero de todo es hacer un análisis previo de los datos, en el cual se realiza una limpieza y balanceo mediante técnicas de UnderSampling.

Todos los resultados obtenidos de los modelos se han mostrado con las métricas de precion, recall, f1score, accuracy y matriz de confusión.
