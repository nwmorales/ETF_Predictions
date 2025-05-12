# Proyecto: Análisis y Predicción de ETFs de EEUU

**Autor/es:** Ivan López Tomàs y Nelson William Morales 

**Repositorio:** https://github.com/nwmorales/ETF_Predictions

---

## 1. Introducción

Los Fondos Cotizados en Bolsa (ETFs) se han consolidado como uno de los instrumentos de inversión más dinámicos y de mayor crecimiento en los mercados financieros globales. Su flexibilidad, diversificación y accesibilidad los han convertido en una opción preferente tanto para inversores institucionales como minoristas, particularmente en el robusto mercado estadounidense. 

El análisis y la predicción del comportamiento de los activos financieros continúan siendo un desafío central y un área de intensa investigación. La capacidad de anticipar movimientos de mercado o identificar patrones subyacentes es crucial para la optimización de estrategias de inversión y la gestión de riesgos.

La Inteligencia Artificial y las tecnologías Big Data en la última década ha abierto nuevas fronteras en este campo. Estas herramientas ofrecen capacidades sin precedentes para procesar y analizar la vasta cantidad de datos generados por los mercados financieros, identificar relaciones no lineales complejas y desarrollar modelos predictivos con un potencial de precisión superior a los enfoques tradicionales.

### Motivación

Los mercados financieros, y en particular los ETFs, ofrecen oportunidades de inversión, pero su comportamiento es complejo y volátil. Predecir sus movimientos es un desafío constante. Este proyecto surge de la necesidad de:

*   Aplicar técnicas de ciencia de datos para entender mejor el comportamiento de los ETFs.
*   Explorar la capacidad predictiva de modelos de Machine Learning sobre datos financieros históricos.
*   Desarrollar una metodología sistemática para la selección de activos (basada en rendimiento pasado) y la posterior modelización.
*   Generar herramientas o insights que *potencialmente* podrían ayudar a fundamentar estrategias de inversión (con las debidas precauciones).

### Objetivos del proyecto

- Este proyecto se centra en el análisis de Fondos Cotizados (ETFs) relevantes del mercado estadounidense. El objetivo principal es identificar los ETFs con mejor rendimiento histórico reciente y utilizar sus datos para construir modelos predictivos que intenten anticipar futuros movimientos del mercado. La finalidad última es explorar la viabilidad de utilizar estos modelos como apoyo en la toma de decisiones de inversión.
  
- El flujo de trabajo abarca desde la obtención y limpieza de datos históricos de ETFs hasta el entrenamiento y evaluación de modelos de Machine Learning para la predicción de precios o tendencias.
  
- Adquirir y preprocesar conjuntos de datos históricos relevantes de una selección de ETFs estadounidenses, utilizando fuentes como Kaggle y la API de Yahoo Finance.

- Realizar un análisis exploratorio exhaustivo de los datos recopilados para identificar características, tendencias y patrones preliminares, empleando herramientas como Pandas en el entorno de Google Colab.

- Diseñar e implementar una arquitectura de Big Data escalable, utilizando Docker para la contenerización, Apache NiFi para la ingesta y el flujo de datos, Apache Cassandra para el almacenamiento de series temporales y Apache Hadoop para el procesamiento y almacenamiento masivo.

- Desarrollar, entrenar y evaluar el rendimiento de modelos de regresión, incluyendo Regresión Lineal y Prophet, para la predicción de la evolución de los precios de los ETFs.

- Implementar y evaluar Redes Neuronales LSTM, para el modelado y predicción del comportamiento de los ETFs.

- Visualizar los datos, los resultados de los análisis y las predicciones de los modelos de manera interactiva y comprensible utilizando Power BI y complementar el análisis con técnicas de minería de datos mediante Orange Datamining.

## 2. Conceptos Fundamentales y Tecnologías Aplicadas

### Fondos Cotizados en Bolsa (ETFs)
Un Fondo Cotizado en Bolsa (ETF, por sus siglas en inglés Exchange-Traded Fund) es un vehículo de inversión colectiva cuyas participaciones se negocian en mercados secundarios de valores, al igual que las acciones. Su objetivo principal suele ser replicar el comportamiento de un determinado índice bursátil, sector económico, materia prima o una cesta diversificada de activos...

La versatilidad de los ETFs se refleja en su amplia tipología, que incluye desde los tradicionales ETFs indexados que siguen índices como el S&P 500 o el NASDAQ 100, hasta ETFs sectoriales, temáticos, de renta fija, e incluso de gestión activa, aunque estos últimos representan una porción menor del mercado...


### Modelos de Predicción Aplicados

#### Regresión Lineal

#### Prophet

#### Redes Neuronales

#### Modelos de Clasificación


### Arquitecturas y Tecnologías Big Data 

#### Apache Hadoop

#### Apache Cassandra

#### Apache NiFi

#### Docker 


### Herramientas de Análisis y Visualización

#### Pandas 

#### Power BI

#### Orange Datamining


## 3. Metodología y Diseño del Sistema

### Adquisición de Datos

#### Fuente de Datos: Kaggle
Una de las fuentes de datos para este proyecto fue un conjunto de datos obtenido de la plataforma Kaggle, denominado 'Nombre del dataset'. Este dataset contenía información histórica de precios [especificar variables] para una selección de [X] ETFs estadounidenses, cubriendo el periodo desde [Fecha Inicio] hasta [Fecha Final]. Los datos se obtuvieron mediante descarga directa del archivo CSV proporcionado en la plataforma.

#### Fuente de Datos: API de Yahoo Finance
Complementariamente, se accedió a datos históricos y actualizados de ETFs mediante la API de Yahoo Finance. Para ello, se utilizó la librería yfinance de Python para realizar consultas programadas. Se seleccionaron [N o criterios] ETFs, incluyendo [mencionar algunos ejemplos clave como SPY, QQQ, etc.], para los cuales se extrajeron datos de precios OHLCV y volumen para el periodo comprendido entre [Fecha Inicio] y [Fecha Final]. Se implementaron [Manejo de errores] para gestionar las limitaciones de frecuencia de la API.


### Preprocesamiento y Análisis Exploratorio de Datos (EDA)

#### Entorno y Herramientas de Preprocesamiento

#### Proceso de Limpieza de Datos

#### Análisis Exploratorio de Datos (EDA)


### Diseño e Implementación de la Arquitectura Big Data

#### Contenerización con Docker

#### Flujo de Datos con Apache NiFi

#### Almacenamiento con Apache Cassandra

#### Almacenamiento y Procesamiento con Apache Hadoop


### Desarrollo y Entrenamiento de Modelos de Predicción


### Uso de Herramientas de Visualización y Minería


### Desafíos Técnicos y Soluciones Implementadas


## 4. Resultados y Pruebas

### Análisis Exploratorio de Datos (EDA)


### Implementación y Pruebas de la Arquitectura Big Data


### Modelos de Predicción


### Visualización y Minería de Datos

## 5. Discusión de Resultados ????


## 6. Conclusiones

https://careers.minsait.com/Minsait/job/Inteligencia-Artificial-Perfil-Junior/978243255/
https://es.trabajo.org/


---
