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


#### Redes Neuronales

##### Que es una red neuronal ?
Una red neuronal artificial (RNA) es un modelo computacional perteneciente al campo del aprendizaje automático, cuyo diseño se inspira en la estructura y funcionamiento del sistema nervioso biológico. Este tipo de arquitectura resulta especialmente eficaz para abordar problemas de alta complejidad que presentan limitaciones para los enfoques algorítmicos tradicionales, como es el caso del reconocimiento de imágenes, el procesamiento del lenguaje natural (PLN) o la traducción automática.

Las redes neuronales están conformadas por unidades elementales denominadas neuronas artificiales, las cuales se agrupan en capas (de entrada, ocultas y de salida) y se interconectan mediante enlaces ponderados. Cada neurona recibe un conjunto de señales de entrada, las procesa mediante una función de activación no lineal y propaga el resultado hacia las neuronas de la capa siguiente. Los pesos asignados a cada conexión cuantifican la influencia de una neurona sobre otra y constituyen los parámetros ajustables del modelo.

Durante la fase de entrenamiento, típicamente mediante algoritmos de optimización basados en retropropagación del error y descenso del gradiente, los pesos son modificados iterativamente con el objetivo de minimizar una función de coste definida sobre un conjunto de datos de entrenamiento. Este mecanismo de ajuste permite a la red neuronal aprender representaciones internas de los datos y generalizar patrones subyacentes, habilitando así su aplicación en tareas de predicción, clasificación o generación de contenido, entre otras.

##### En nuestro caso en concreto usamos una Red Neuronal Recurrente o RNN
##### *¿Qué es un modelo de predicción basado en una Red Neuronal Recurrente (RNN)?*

Una Red Neuronal Recurrente (RNN) es un tipo de red neuronal diseñada específicamente para procesar secuencias de datos, donde el orden y la dependencia temporal entre los elementos son importantes. A diferencia de las redes neuronales feedforward tradicionales, las RNN tienen conexiones que forman ciclos, lo que les permite mantener un estado interno (memoria) que captura información sobre las entradas pasadas en la secuencia.

En el contexto de la predicción de series temporales como los precios de ETFs, una RNN puede aprender patrones y dependencias a lo largo del tiempo.
La arquitectura básica de una RNN implica que la salida de una capa en un paso de tiempo se alimenta de nuevo a la misma capa en el siguiente paso de tiempo. Esto permite que la red "recuerde" información de pasos anteriores en la secuencia.

_LSTM (Long Short-Term Memory): Una RNN con Memoria a Largo Plazo_

Aunque las RNN teóricamente pueden aprender dependencias a largo plazo, en la práctica, las RNN simples sufren de un problema conocido como el "desvanecimiento del gradiente" (y el problema opuesto, la "explosión del gradiente"). Esto dificulta que la red aprenda y retenga información de pasos de tiempo muy lejanos en la secuencia.

Las redes LSTM son una arquitectura especial de RNN diseñada para superar estos problemas y capturar dependencias a largo plazo de manera más efectiva. Introducen un mecanismo llamado "celda de memoria" y "puertas" (gates) que controlan el flujo de información dentro de la red.
Estas puertas utilizan funciones sigmoideas para producir valores entre 0 y 1, actuando como interruptores que modulan el flujo de información. La combinación de estas puertas permite a las LSTM aprender cuándo retener información importante durante largos períodos y cuándo descartar información irrelevante.

*¿Para qué sirve un modelo basado en una Red Neuronal Recurrente (LSTM) en la predicción de valores de ETFs?*

En la predicción de valores futuros de ETFs, un modelo LSTM puede ser muy útil por su capacidad para:

- Capturar dependencias temporales complejas: Los precios de los ETFs están influenciados por una compleja interacción de factores a lo largo del tiempo. Las LSTM pueden aprender patrones secuenciales que podrían ser difíciles de capturar con modelos lineales como la regresión lineal. Por ejemplo, podrían identificar patrones de volatilidad, tendencias a corto y mediano plazo, y posibles efectos de "momentum".
- Modelar la volatilidad: Aunque no modelan directamente la volatilidad como algunos modelos específicos (como los modelos GARCH), las LSTM pueden aprender patrones en la volatilidad histórica y, potencialmente, predecir cambios en la volatilidad futura.
- Manejar secuencias de entrada largas: La capacidad de las LSTM para retener información a largo plazo les permite procesar secuencias de precios históricos más extensas y capturar dependencias que se extienden durante períodos de tiempo más largos.
- Incorporar múltiples variables de entrada: Al igual que la regresión lineal, las LSTM pueden tomar múltiples series temporales como entrada (por ejemplo, precios históricos del ETF, volúmenes, precios de otros activos relacionados, indicadores técnicos) para realizar la predicción. La red puede aprender las complejas interrelaciones temporales entre estas variables y el precio futuro del ETF.
  
_Puntos fuertes de un modelo basado en LSTM en el contexto de la predicción de ETFs:_

* Capacidad para aprender dependencias a largo plazo: Esta es la principal ventaja de las LSTM sobre las RNN simples y los modelos tradicionales de series temporales. Pueden capturar patrones que se desarrollan durante períodos de tiempo extensos.
* Manejo de secuencias complejas: Las LSTM son capaces de modelar relaciones no lineales y dependencias temporales intrincadas que pueden existir en los mercados financieros.
* Adaptabilidad a diferentes patrones: La arquitectura flexible de las LSTM les permite adaptarse a una variedad de patrones y dinámicas en los datos del precio del ETF.
* Potencial para mejorar la precisión en mercados volátiles: En mercados con alta volatilidad y patrones complejos, las LSTM podrían superar a modelos más simples que asumen linealidad o dependencias temporales más cortas.
  

### Diferencias y similitudes clave entre un modelo de regresión lineal y una red neuronal artificial (RNA)

Las Similitudes principales són las siguientes:

* Modelo paramétrico supervisado: Ambos enfoques pertenecen a la categoría de modelos de aprendizaje supervisado y requieren un conjunto de datos etiquetado para su entrenamiento. Además, son modelos paramétricos, es decir, aprenden una serie de parámetros (pesos) que definen la relación entre las variables de entrada y la salida.
* Función de salida basada en una combinación lineal de entradas: En su forma más básica, una neurona artificial realiza una combinación lineal de las entradas ponderadas por sus respectivos pesos, lo cual es conceptualmente equivalente a la formulación de la regresión lineal. En una red neuronal de una sola capa y sin funciones de activación no lineales, el comportamiento del modelo es efectivamente el de una regresión lineal.
* Optimización mediante descenso del gradiente: Ambos modelos pueden entrenarse mediante métodos de optimización basados en descenso del gradiente para minimizar una función de pérdida (por ejemplo, el error cuadrático medio).

Las diferencias principales por otro lado són:

* Capacidad de modelado no lineal: La regresión lineal modela únicamente relaciones lineales entre las variables de entrada y la salida. Por el contrario, las redes neuronales incorporan funciones de activación no lineales (como ReLU, sigmoide, tanh), lo que les permite aproximar funciones no lineales complejas y capturar relaciones de mayor nivel entre las variables.
* Arquitectura del modelo: La regresión lineal consiste en una única combinación lineal de entradas (una sola capa sin no linealidades), mientras que una red neuronal puede tener múltiples capas ocultas (modelo de red neuronal profunda o deep learning), lo que la convierte en un modelo jerárquico capaz de aprender representaciones de alto nivel.
* Capacidad de generalización y expresividad: Las redes neuronales, debido a su arquitectura más compleja, tienen una mayor capacidad de representación (teóricamente, pueden aproximar cualquier función continua bajo ciertas condiciones, como establece el teorema de aproximación universal). Esto las hace más adecuadas para tareas como visión por computador o procesamiento de lenguaje, mientras que la regresión lineal se queda limitada a contextos donde las relaciones sean más simples y lineales.
* Requisitos computacionales y entrenamiento: Entrenar una red neuronal es computacionalmente más costoso y requiere técnicas adicionales como regularización (dropout, L2), optimizadores avanzados (Adam, RMSprop), y puede presentar problemas como el sobreajuste o el estancamiento del gradiente. En cambio, la regresión lineal tiene una solución analítica cerrada en muchos casos, y su entrenamiento es considerablemente más eficiente y estable.
* Interpretabilidad: La regresión lineal ofrece una interpretación directa y clara de los coeficientes como la influencia marginal de cada variable sobre la salida, lo cual es útil para análisis explicativo. Las redes neuronales, por su complejidad, se consideran modelos de caja negra, donde la interpretación de los pesos no es trivial y a menudo se requiere el uso de técnicas específicas de interpretabilidad (SHAP, LIME, saliency maps, etc.).

### En la siguiente tabla se presenta una comparación entre el modelo de regresión lineal y una red neuronal artificial, destacando sus principales similitudes y diferencias en términos de capacidad de modelado, arquitectura, interpretabilidad y aplicaciones.

### Comparativa entre Red Neuronal Artificial (RNA) y Regresión Lineal

| Aspecto                                   | Regresión Lineal                                                                 | Red Neuronal Artificial (RNA)                                                      |
|------------------------------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| **Tipo de modelo**                        | Supervisado, paramétrico                                                         | Supervisado, paramétrico                                                           |
| **Relación entre variables**              | Lineal                                                                           | Puede modelar relaciones no lineales                                               |
| **Arquitectura**                          | Una sola capa (modelo plano)                                                     | Múltiples capas (modelo jerárquico, deep learning)                                 |
| **Función de salida**                     | Combinación lineal de entradas                                                    | Combinación lineal seguida de funciones de activación no lineales                  |
| **Capacidad de representación**           | Limitada a relaciones lineales                                                   | Capacidad universal de aproximación de funciones complejas                         |
| **Método de entrenamiento**               | Solución analítica (cuando es posible) o descenso del gradiente                   | Descenso del gradiente con retropropagación, optimización iterativa               |
| **Computación y recursos**                | Requiere pocos recursos computacionales                                          | Requiere mayor capacidad computacional (CPU/GPU)                                   |
| **Interpretabilidad**                     | Alta: coeficientes directamente interpretables                                   | Baja: modelo tipo “caja negra”; requiere técnicas específicas de interpretabilidad |
| **Riesgo de sobreajuste**                 | Bajo en general                                                                  | Alto si no se regula adecuadamente                                                 |
| **Ámbitos de aplicación**                 | Problemas con relaciones lineales claras (predicción simple, análisis explicativo) | Tareas complejas como visión por computador, PLN, clasificación no lineal         |



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
Una de las fuentes primarias de datos para el presente proyecto fue la plataforma Kaggle, reconocida como un importante repositorio en línea de datasets públicos y una comunidad para profesionales de la ciencia de datos. Específicamente, se utilizó el conjunto de datos titulado "Mutual Funds and ETFs", aportado por el usuario Stefano Leone (stefanoleone992) [1]. Dentro de este conjunto de datos más amplio, el análisis y las predicciones desarrolladas en este trabajo se centran exclusivamente en la información contenida en el archivo ETF prices.csv.

El archivo ETF prices.csv contiene precios históricos diarios y volumen de negociación para una extensa colección de Fondos Cotizados en Bolsa (ETFs). Si bien el dataset general también incluye fondos mutuos, este archivo se enfoca específicamente en ETFs que, dado el contexto del conjunto de datos, están predominantemente listados y negociados en mercados de Estados Unidos (EEUU). Esto proporciona una amplia gama de instrumentos que abarcan diversos índices, sectores (como tecnología, salud, finanzas), clases de activos (renta variable, renta fija, etc.) y estrategias de inversión dentro del mercado estadounidense.

Las variables (columnas) principales identificadas y utilizadas de este archivo para el análisis son las siguientes:

- fund_symbol: (Texto) Símbolo o ticker del ETF, que actúa como identificador único en el mercado.
- price_date: (Fecha) Fecha específica, en formato AAAA-MM-DD, a la que corresponden los datos de la fila.
- open: (Numérico) Precio de apertura del ETF en la jornada bursátil de price_date.
- high: (Numérico) Precio máximo alcanzado por el ETF durante la sesión de price_date.
- low: (Numérico) Precio mínimo alcanzado por el ETF durante la sesión de price_date.
- close: (Numérico) Precio del ETF al cierre de la jornada bursátil de price_date.
- adj_close: (Numérico) Precio de cierre ajustado. Este valor es fundamental para el análisis de rendimientos, ya que se corrige para reflejar eventos corporativos como el pago de dividendos y desdoblamientos de acciones (splits), ofreciendo una representación más precisa de la rentabilidad real de la inversión.
- volume: (Numérico Entero) Número total de acciones del ETF negociadas durante la sesión en price_date, siendo un indicador clave de la liquidez del activo.
- Los datos contenidos en el archivo ETF prices.csv cubren un extenso periodo histórico, abarcando desde el 29 de enero de 1993 hasta el 27 de marzo de 2024. Es relevante destacar que no todos los ETFs presentan datos para la totalidad de este intervalo, ya que la disponibilidad de su historial depende de la - fecha de creación o liquidación de cada fondo específico.

La obtención del archivo ETF prices.csv se realizó mediante la descarga manual directa desde la página del dataset "Mutual Funds and ETFs" en la plataforma Kaggle, accesible en https://www.kaggle.com/datasets/stefanoleone992/mutual-funds-and-etfs/data.

Una observación inicial del archivo ETF prices.csv revela su considerable tamaño, con aproximadamente 1.295.490  millones de filas (registros) según la información proporcionada en Kaggle. Este volumen de datos sugiere la inclusión de un número significativo de ETFs diferentes. Asimismo, la variabilidad en la longitud de las series temporales históricas para cada ETF fue una característica anticipada y considerada para la posterior fase de preprocesamiento y selección de datos para el modelado. También se tuvo en cuenta la posible presencia de valores ausentes (NaNs) en algunas columnas, un aspecto común en datos financieros que requiere un tratamiento específico.


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
