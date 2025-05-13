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

##### ¿Qué es un modelo de predicción basado en una Regresión Lineal?

Un modelo de Regresión Lineal es un algoritmo fundamental en estadística y aprendizaje automático que busca modelar la relación lineal entre una variable dependiente (en tu caso, el precio futuro del ETF) y una o más variables independientes o predictoras (que podrían ser precios históricos del ETF, volúmenes de negociación, indicadores macroeconómicos, etc.).

El objetivo del modelo de regresión lineal es encontrar los valores de los coeficientes (![image](https://github.com/user-attachments/assets/f2a95ccf-32af-44e5-89ed-405312612616)) que mejor se ajusten a los datos históricos, minimizando la suma de los errores al cuadrado (método de mínimos cuadrados ordinarios - OLS). Una vez entrenado el modelo con datos históricos, se pueden utilizar los coeficientes aprendidos para predecir valores futuros de la variable dependiente basándose en los valores futuros de las variables predictoras.

##### ¿Hasta donde llega la utilidad del modelo de Regresión Lineal en la predicción de valores de ETFs?

En la predicción de valores futuros de ETFs, un modelo de regresión lineal puede utilizarse de diversas maneras, dependiendo de las variables predictoras que se incluyan:

* Predicción basada en precios históricos: La forma más simple sería utilizar precios históricos del propio ETF como variable predictora (por ejemplo, el precio de ayer para predecir el precio de hoy, o un promedio de precios pasados). Esto se asemeja a algunos enfoques básicos de análisis técnico.
Como es nuestro modelo.
*  Incorporación de otras variables financieras: Se pueden incluir otras variables financieras que se consideren relevantes para el precio del ETF, como:
  - Índices de referencia: El rendimiento del índice subyacente del ETF (por ejemplo, el S&amp;P 500 para un ETF que lo rastrea).
  - Precios de activos relacionados: Los precios de acciones individuales dentro del ETF o de otros ETFs relacionados.
  - Volúmenes de negociación: El volumen de acciones del ETF negociadas.
  - Tasas de interés: Las tasas de interés pueden influir en el atractivo de diferentes clases de activos.
  - Tipos de cambio: Relevante para ETFs que invierten en activos extranjeros.
* Incorporación de indicadores macroeconómicos: Variables como el PIB, la inflación, las tasas de desempleo, los índices de confianza del consumidor, etc., podrían utilizarse para modelar tendencias a largo plazo o efectos cíclicos en el precio del ETF.

El modelo de regresión lineal busca identificar y cuantificar la relación lineal entre estas variables predictoras y el precio futuro del ETF. Una vez entrenado, se pueden ingresar los valores futuros estimados de las variables predictoras para obtener una predicción del precio del ETF.

##### Puntos fuertes de un modelo de Regresión Lineal en el contexto de la predicción de ETFs:

* Simplicidad e interpretabilidad: Los modelos de regresión lineal son relativamente fáciles de entender e interpretar. Los coeficientes (β) indican la dirección y la magnitud del efecto de cada variable predictora sobre la variable dependiente. Esto puede proporcionar información valiosa sobre los factores que influyen en el precio del ETF.
* Rapidez y eficiencia: El entrenamiento y la predicción con modelos de regresión lineal son computacionalmente eficientes, incluso con grandes conjuntos de datos.
Base estadística sólida: La regresión lineal tiene una base estadística bien establecida, con métricas y pruebas para evaluar la bondad del ajuste del modelo y la significancia de las variables predictoras (por ejemplo, R-cuadrado, pruebas t, pruebas F).
* Flexibilidad en la inclusión de variables: Permite incorporar una amplia variedad de variables predictoras que se consideren relevantes para el precio del ETF.
Puede capturar relaciones lineales: Si la relación entre las variables predictoras y el precio del ETF es aproximadamente lineal, la regresión lineal puede proporcionar buenas predicciones.

#### Prophet

##### ¿Qué es el modelo de predicción Prophet?

Prophet es un modelo de previsión desarrollado por Facebook (ahora Meta) y diseñado principalmente para series temporales con fuertes patrones de estacionalidad (como patrones diarios, semanales y anuales) y que pueden verse afectadas por eventos irregulares o festivos. A diferencia de algunos modelos tradicionales de series temporales como ARIMA, Prophet adopta un enfoque aditivo donde descompone la serie temporal en varios componentes:

* Tendencia (g(t)): Modela los cambios no periódicos en el valor de la serie temporal. Prophet implementa por defecto una tendencia lineal por partes, pero también permite una tendencia logística para modelar efectos de saturación.

* Estacionalidad (s(t)): Representa los patrones periódicos, como la estacionalidad diaria, semanal y anual. Prophet utiliza series de Fourier para modelar estos efectos, lo que le permite adaptarse a múltiples periodos de estacionalidad simultáneamente.

* Festivos (h(t)): Permite incorporar el impacto de eventos específicos y predecibles (como días festivos, lanzamientos de productos, etc.) que pueden afectar la serie temporal. El usuario debe proporcionar una lista de estos eventos y sus fechas.

* Término de error (Et): Representa el ruido aleatorio que no se explica por los otros componentes del modelo.

##### ¿Para qué sirve Prophet en nuestro caso, enfocado la predicción de valores de ETFs?

En el contexto específico de la predicción de valores futuros de acciones de ETFs, Prophet puede ser útil por varias razones:

1. Primeramente, este captura la estacionalidad: A que me refiero, aunque los mercados financieros no siempre presentan una estacionalidad tan marcada como, por ejemplo, las ventas minoristas, pueden existir patrones semanales (efectos de fin de semana) o incluso anuales sutiles relacionados con ciclos económicos o comportamiento de inversores. Prophet puede intentar identificar y modelar estos patrones.
2. Por otro lado, ofrece la opción de manejar las tendencias: Los precios de los ETFs obviamente tienen tendencias a largo plazo influenciadas por el rendimiento de los activos subyacentes, las condiciones económicas generales y el sentimiento del mercado. Prophet puede modelar estas tendencias, aunque su capacidad para predecir cambios bruscos en la tendencia (como los causados por eventos inesperados) es limitada.
3. Además, también incorpora en el modelo la variable de los eventos conocidos: Si bien es difícil predecir eventos futuros que impacten significativamente el mercado, Prophet permite incorporar el efecto de eventos pasados conocidos (como anuncios de políticas económicas, resultados empresariales importantes dentro del ETF, etc.) si se dispone de datos sobre su impacto. Esto puede ayudar a mejorar el ajuste del modelo a la historia.
4. Robustez y facilidad del uso de este modelo: Prophet es relativamente robusto ante datos faltantes y cambios en la varianza de la serie temporal. Además, su API en Python y R es bastante intuitiva, lo que facilita su implementación y ajuste, incluso para usuarios con menos experiencia en modelado de series temporales.
5. Otro gran punto a favor de este modelo frente a otros, es, la generación de intervalos de incertidumbre: Prophet proporciona intervalos de confianza para sus predicciones, lo que te da una idea del rango de posibles valores futuros y te ayuda a evaluar la incertidumbre asociada a la predicción.
6. Velocidad y escalabilidad es otro de los factores positivos que te presenta este modelo: Prophet está diseñado para manejar grandes conjuntos de datos y realizar predicciones de manera eficiente, lo cual puede ser útil si estás trabajando con muchos ETFs o con series temporales largas.
7. Y finalmente otra de las grandes virtudes que proporciona el prohet para la predicción de valores es, el manejo que tr ofrece frente a los datos faltantes: Prophet puede manejar razonablemente bien los datos faltantes en la serie temporal sin necesidad de imputación previa.
Sin embargo, es crucial tener en cuenta las limitaciones de Prophet al predecir valores de ETFs:

#### Redes Neuronales

#### Modelos de Clasificación


### Arquitecturas y Tecnologías Big Data 

#### Apache Hadoop
El ecosistema Apache Hadoop representa una solución de código abierto fundamental en el mundo del Big Data, proporcionando herramientas para el almacenamiento y procesamiento distribuido de conjuntos de datos a gran escala. Dentro de este ecosistema, el Hadoop Distributed File System (HDFS) destaca como su componente principal de almacenamiento. HDFS es un sistema de archivos diseñado específicamente para almacenar archivos muy grandes de forma fiable a través de clústeres de máquinas estándar. Su arquitectura se basa en la división de los archivos en bloques de gran tamaño que se distribuyen y, crucialmente, se replican en múltiples nodos (DataNodes) del clúster. Esta replicación (cuyo factor es configurable) es la clave de su alta tolerancia a fallos, ya que asegura que la pérdida de un nodo individual no resulte en la pérdida de datos.

HDFS por sí mismo cumple un rol esencial como repositorio de datos masivo, escalable y relativamente económico. En muchas arquitecturas Big Data, HDFS actúa como el "Data Lake" o almacén central donde se depositan grandes cantidades de datos brutos o semi-procesados para su conservación a largo plazo y para servir como fuente para análisis posteriores o entrenamientos de modelos complejos


#### Apache Cassandra
Apache Cassandra es un sistema de gestión de bases de datos NoSQL distribuido y de código abierto, diseñado específicamente para manejar grandes volúmenes de datos con altos requisitos de disponibilidad y escalabilidad, operando sobre clústeres de hardware estándar. Su arquitectura distribuida, sin un único punto de fallo (peer-to-peer), y su mecanismo de replicación de datos le confieren una robusta tolerancia a fallos y la capacidad de mantener la alta disponibilidad del servicio incluso si fallan nodos individuales en el clúster.

Estas capacidades hacen que Cassandra sea particularmente valiosa en el sector financiero y en arquitecturas Big Data para casos de uso como:

- Almacenamiento y consulta eficiente de datos de series temporales: Ideal para precios de mercado, logs de transacciones, y otros datos indexados por tiempo donde se necesita tanto una ingesta rápida como un acceso veloz a rangos específicos
- Servir como base de datos operacional "caliente": Actuando como el almacén para los datos de acceso más frecuente o reciente, que alimentan aplicaciones, dashboards o procesos de predicción que requieren respuestas rápidas

  
#### Apache NiFi
Apache NiFi es una plataforma de software de código abierto, integrada en el ecosistema de la Apache Software Foundation, diseñada específicamente para automatizar y gestionar el flujo de datos (DataFlow) entre sistemas heterogéneos de forma fiable y escalable. Su principal característica distintiva es su interfaz gráfica de usuario basada en web, que permite a los usuarios diseñar visualmente complejos pipelines de datos mediante la conexión de "Procesadores". Estos procesadores son componentes modulares que realizan tareas específicas como la ingesta de datos desde diversas fuentes (ej., monitorizando directorios con GetFile o consumiendo APIs), la transformación de datos en ruta (ej., modificando esquemas o convirtiendo tipos de datos con UpdateRecord), y el enrutamiento inteligente de la información hacia uno o múltiples destinos (ej., PutHDFS, PutCassandraQL).

Por estas razones, NiFi se posiciona como un orquestador y preparador de datos muy eficaz en arquitecturas Big Data, especialmente en casos de uso que requieren:
- La integración de datos provenientes de múltiples fuentes con diferentes formatos o protocolos.
- La aplicación de transformaciones o limpiezas preliminares antes de que los datos lleguen a los sistemas de almacenamiento o análisis.
- La distribución fiable de datos a diferentes sistemas (ej., un data lake en HDFS para histórico y una base de datos NoSQL como Cassandra para acceso rápido).


#### Docker 
Docker es una plataforma de código abierto que ha revolucionado la forma en que se desarrollan, distribuyen y ejecutan las aplicaciones mediante el uso de la tecnología de contenerización. La idea central es empaquetar una aplicación o servicio, junto con todas sus dependencias (librerías, binarios, archivos de configuración, etc.), en una unidad estandarizada y aislada denominada contenedor. Estos contenedores se crean a partir de imágenes (plantillas de solo lectura) y se ejecutan de manera consistente en cualquier máquina que tenga Docker instalado, independientemente del sistema operativo subyacente o de otras aplicaciones que se estén ejecutando. Para gestionar aplicaciones que constan de múltiples servicios interconectados (como una arquitectura Big Data), herramientas como Docker Compose permiten definir y ejecutar aplicaciones multi-contenedor a partir de un único archivo de configuración (docker-compose.yml).

Docker se ha convertido en una herramienta prácticamente indispensable en el desarrollo y despliegue de proyectos complejos de Big Data e Inteligencia Artificial por varias razones clave:
- Simplificación de la Configuración y el Despliegue: Montar entornos que involucran múltiples componentes de Big Data (como pueden ser clústeres de Hadoop, bases de datos NoSQL como Cassandra, herramientas de flujo como NiFi, etc.) puede ser un proceso manual complejo y propenso a errores. Docker y Docker Compose simplifican radicalmente este proceso, permitiendo levantar una arquitectura completa con todos sus servicios interconectados mediante unos pocos comandos
- Aislamiento de Servicios: Cada contenedor se ejecuta en su propio entorno aislado, con sus propios recursos (sistema de archivos, red, procesos), evitando conflictos de dependencias o puertos entre diferentes servicios que se ejecutan en la misma máquina host.
- Portabilidad: Las imágenes de Docker pueden construirse en una máquina y ejecutarse en cualquier otra (local, servidor, nube) que soporte Docker, facilitando la migración entre entornos.

### Herramientas de Análisis y Visualización

#### Pandas 

#### Power BI
Microsoft Power BI es un servicio de análisis de negocios que forma parte de la plataforma Power Platform de Microsoft, diseñado para proporcionar capacidades de inteligencia empresarial (Business Intelligence) y visualizaciones de datos interactivas. Power BI ofrece herramientas para la transformación y modelado de los mismos (a través de Power Query y DAX - Data Analysis Expressions), aunque su principal fortaleza reconocida radica en la creación de informes y dashboards visualmente atractivos y dinámicos.

La plataforma se destaca por su interfaz intuitiva que facilita la creación de una amplia gama de objetos visuales, como gráficos de líneas, barras, áreas, circulares, mapas, tablas, matrices y tarjetas de indicadores clave de rendimiento (KPIs).


#### Orange Datamining
Orange Datamining es una potente plataforma de software de código abierto, desarrollada en Python, que facilita el análisis de datos, la minería de datos y el aprendizaje automático (_Machine Learning_). Los usuarios construyen análisis complejos mediante la conexión de componentes visuales, conocidos como "widgets", en un lienzo de flujo de trabajo (_workflow_). Cada widget encapsula una operación específica, abarcando el ciclo de vida completo del análisis de datos: desde la carga de datos (_widget File_), la exploración visual interactiva (_widgets como Distributions, Correlations, Scatter Plot_), el preprocesamiento de datos (_incluyendo selección de características con Select Columns o transformaciones como codificación one-hot y escalado con Continuize_), la aplicación de una amplia gama de algoritmos de modelado (_regresión como Linear Regression, Tree, Random Forest, Gradient Boosting, así como clasificación y clustering_), hasta la evaluación rigurosa de modelos (_widget Test & Score con opciones como validación cruzada_) y el análisis detallado de resultados (_visualización de predicciones, importancia de variables con Rank, o inspección de modelos como con Tree Viewer_).

Las principales ventajas de este enfoque visual e integrado, especialmente relevantes en el ámbito del análisis de datos y la IA, incluyen:
- Accesibilidad y Curva de Aprendizaje: Facilita la comprensión y aplicación de técnicas complejas tanto para usuarios nuevos como para expertos que buscan rapidez.
- Rapidez de Prototipado y Experimentación: Permite construir, modificar y comparar diferentes flujos de trabajo de preprocesamiento y modelado de forma muy ágil, conectando y desconectando widgets.
- Interactividad y Comprensión: La capacidad de inspeccionar los datos o los resultados intermedios en casi cualquier punto del flujo de trabajo fomenta una comprensión más profunda del proceso y de los datos mismos.

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
