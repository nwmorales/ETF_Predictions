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




### Apartado Y: Modelo de Predicción Aplicado – Regresión Lineal

#### Y.1 Justificación y Selección del Modelo

Dentro del conjunto de técnicas de modelado predictivo evaluadas en este proyecto, se implementó el modelo de **Regresión Lineal (RL)**. La elección de este modelo se fundamenta en:

*   **Objetivo del Proyecto:** La necesidad de modelar una relación potencialmente lineal entre nuestra variable objetivo continua, **`[Nombre de tu variable dependiente Y]`**, y un conjunto de predictores, **`[Menciona brevemente tus variables independientes X clave]`**.
*   **Análisis Exploratorio Previo:** Los análisis exploratorios iniciales (ver `Apartado Z: Análisis Exploratorio de Datos`) sugirieron la existencia de tendencias lineales entre `[Variable Y]` y algunas de las variables predictoras como `[Ejemplo: Superficie, Antigüedad]`.
*   **Interpretabilidad:** La alta interpretabilidad de los coeficientes de la RL resulta valiosa para comprender el impacto individual estimado de cada predictor sobre `[Variable Y]`, un aspecto relevante para los objetivos de este estudio.
*   **Benchmark:** Su simplicidad y eficiencia computacional lo convierten en un excelente modelo de referencia (`baseline`) para comparar el rendimiento de algoritmos más complejos que se exploran en apartados posteriores.
*   **Naturaleza del Problema:** El problema de predecir `[Variable Y]` se alinea bien con el marco de la regresión supervisada para variables continuas.

#### Y.2 Fundamento Teórico y Formulación Específica

La Regresión Lineal postula que la relación entre la variable dependiente (`Y`) y una o más variables independientes (`X₁`, `X₂`, ..., `Xₚ`) puede aproximarse mediante una función lineal. En este proyecto, se aplicó la **[Elige: Regresión Lineal Simple / Regresión Lineal Múltiple]**.

*   **[Si es Simple]:** Se buscó modelar `[Variable Y]` utilizando únicamente `[Variable X única]` mediante la ecuación:
    ```
    [Variable Y] = β₀ + β₁[Variable X única] + ε
    ```
*   **[Si es Múltiple]:** Se modeló `[Variable Y]` utilizando el conjunto de predictores `[Lista tus variables X₁, X₂, ..., Xₚ]` mediante la ecuación:
    ```
    [Variable Y] = β₀ + β₁[Variable X₁] + β₂[Variable X₂] + ... + βₚ[Variable Xₚ] + ε
    ```

Donde:
*   `β₀` representa el valor esperado de `[Variable Y]` cuando todos los predictores son cero (o el valor base si las variables están centradas/escaladas).
*   `βᵢ` (para `i ≥ 1`) es el coeficiente asociado a la variable predictora `[Variable Xᵢ]`. Estima el cambio esperado en `[Variable Y]` por cada unidad de cambio en `[Variable Xᵢ]`, manteniendo constantes las demás variables predictoras incluidas en el modelo (*ceteris paribus*).
*   `ε` es el término de error o residuo, que captura la variabilidad de `[Variable Y]` no explicada por la relación lineal con los predictores incluidos.

#### Y.3 Estimación del Modelo: Método de Mínimos Cuadrados Ordinarios (MCO)

Para determinar los valores óptimos de los coeficientes (`β₀, β₁, ..., βₚ`) que mejor ajustan el modelo a nuestros datos de entrenamiento, se empleó el método de **Mínimos Cuadrados Ordinarios (MCO)** u *Ordinary Least Squares (OLS)*. Este método minimiza la Suma de los Cuadrados de los Residuos (SCR), es decir, la suma de las diferencias al cuadrado entre los valores observados de `[Variable Y]` (`Yᵢ`) y los valores predichos por el modelo (`Ŷᵢ`):

```math
Minimizar \ SCR = \sum_{i=1}^{n}(Yᵢ - Ŷᵢ)² = \sum_{i=1}^{n}(Yᵢ - (β₀ + β₁[Variable X₁ᵢ] + ... + βₚ[Variable Xₚᵢ]))²


El modelo final de Regresión Lineal obtenido (o el más representativo) fue:
Ŷ = [Valor de β₀] + [Valor de β₁]*[Variable X₁] + ... + [Valor de βₚ]*[Variable Xₚ]



#### Prophet

#### Redes Neuronales

#### Modelos de Clasificación


### Arquitecturas y Tecnologías Big Data 

#### Apache Hadoop
El ecosistema Apache Hadoop representa una solución de código abierto fundamental en el mundo del Big Data, proporcionando herramientas para el almacenamiento y procesamiento distribuido de conjuntos de datos a gran escala. Dentro de este ecosistema, el Hadoop Distributed File System (HDFS) destaca como su componente principal de almacenamiento. HDFS es un sistema de archivos diseñado específicamente para almacenar archivos muy grandes de forma fiable a través de clústeres de máquinas estándar. Su arquitectura se basa en la división de los archivos en bloques de gran tamaño que se distribuyen y, crucialmente, se replican en múltiples nodos (DataNodes) del clúster. Esta replicación (cuyo factor es configurable) es la clave de su alta tolerancia a fallos, ya que asegura que la pérdida de un nodo individual no resulte en la pérdida de datos.

HDFS por sí mismo cumple un rol esencial como repositorio de datos masivo, escalable y relativamente económico. En muchas arquitecturas Big Data, HDFS actúa como el "Data Lake" o almacén central donde se depositan grandes cantidades de datos brutos o semi-procesados para su conservación a largo plazo y para servir como fuente para análisis posteriores o entrenamientos de modelos complejos


#### Apache Cassandra
Apache Cassandra es un sistema de gestión de bases de datos NoSQL distribuido y de código abierto, diseñado específicamente para manejar grandes volúmenes de datos con altos requisitos de disponibilidad y escalabilidad, operando sobre clústeres de hardware estándar. Su arquitectura distribuida, sin un único punto de fallo (peer-to-peer), y su mecanismo de replicación de datos le confieren una robusta tolerancia a fallos y la capacidad de mantener la alta disponibilidad del servicio incluso si fallan nodos individuales en el clúster.
Complementando su fortaleza en escrituras, Cassandra ofrece lecturas de muy baja latencia cuando las consultas están bien definidas y se basan en la clave primaria. 
Estas capacidades hacen que Cassandra sea particularmente valiosa en el sector financiero y en arquitecturas Big Data para casos de uso como:
#### Apache NiFi

#### Docker 
La contenerización mediante Docker fue adoptada en este proyecto para asegurar la consistencia y reproducibilidad del entorno de desarrollo y despliegue de los distintos componentes de la arquitectura Big Data, incluyendo NiFi, Cassandra y los nodos de Hadoop. Esto simplifica la gestión de dependencias y facilita la portabilidad de la solución.

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
