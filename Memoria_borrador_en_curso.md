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

## Conceptos Fundamentales y Tecnologías Aplicadas

### Fondos Cotizados en Bolsa (ETFs)
Un Fondo Cotizado en Bolsa (ETF, por sus siglas en inglés Exchange-Traded Fund) es un vehículo de inversión colectiva cuyas participaciones se negocian en mercados secundarios de valores, al igual que las acciones. Su objetivo principal suele ser replicar el comportamiento de un determinado índice bursátil, sector económico, materia prima o una cesta diversificada de activos...

La versatilidad de los ETFs se refleja en su amplia tipología, que incluye desde los tradicionales ETFs indexados que siguen índices como el S&P 500 o el NASDAQ 100, hasta ETFs sectoriales, temáticos, de renta fija, e incluso de gestión activa, aunque estos últimos representan una porción menor del mercado...

### Modelos de Predicción Aplicados
    * **2.3.1. Regresión Lineal**
        * **Fundamento:** Modelo que establece una relación lineal entre una variable dependiente y una o más independientes (<span class="math-inline">Y \= \\beta\_0 \+ \\sum \\beta\_i X\_i \+ \\epsilon</span>).
        * **Aplicación en Finanzas/Series Temporales:** Predicción de tendencias, análisis de factores. Limitaciones con datos no estacionarios o relaciones no lineales.
        * **Ventajas:** Simplicidad, interpretabilidad de los coeficientes.
        * **Desventajas:** Suposiciones restrictivas, a menudo demasiado simple para la complejidad de los mercados.
    * **2.3.2. Modelo Prophet**
        * **Fundamento:** Modelo aditivo descomponible (<span class="math-inline">y\(t\) \= g\(t\) \+ s\(t\) \+ h\(t\) \+ \\epsilon\_t</span>), donde <span class="math-inline">g\(t\)</span> es la tendencia (lineal o logística por tramos), <span class="math-inline">s\(t\)</span> las estacionalidades (Fourier series), y <span class="math-inline">h\(t\)</span> los efectos de festivos.
        * **Aplicación:** Series temporales con patrones estacionales claros, robusto a outliers y datos faltantes.
        * **Ventajas:** Fácil de usar, parámetros intuitivos, buen manejo de múltiples estacionalidades y festivos.
        * **Desventajas:** Puede ser menos flexible para tendencias muy complejas o interacciones no modeladas explícitamente.
    * **2.3.3. Redes Neuronales (Ej. si usaste LSTM)**
        * **Fundamento (General NN y del tipo específico):**
            * *General:* Modelos de aprendizaje inspirados en redes neuronales biológicas, capaces de aprender funciones complejas y no lineales a partir de los datos.
            * *LSTM:* Tipo de Red Neuronal Recurrente (RNN) diseñada para modelar secuencias y capturar dependencias a largo plazo mediante celdas con compuertas de memoria (entrada, olvido, salida).
        * **Aplicación en Finanzas/Series Temporales:** Predicción de precios, volatilidad, análisis de sentimiento. Especialmente LSTMs para datos secuenciales.
        * **Ventajas:** Gran capacidad para modelar no linealidades y dependencias complejas; las LSTMs manejan bien secuencias largas.
        * **Desventajas:** Requieren muchos datos y recursos computacionales, "caja negra" (difícil interpretación directa), propensas al sobreajuste si no se regularizan bien.
    * **2.3.4. Modelos de Clasificación (Debes listar y describir brevemente CADA UNO que usaste. Ej. Random Forest)**
        * **Fundamento (General de Clasificación y del modelo específico):**
            * *General:* El objetivo es asignar una instancia a una categoría o clase predefinida.
            * *Random Forest (ejemplo):* Método de ensamble que construye múltiples árboles de decisión a partir de submuestras bootstrap de los datos y promediando (o votando) sus predicciones para mejorar la robustez y precisión.
        * **Aplicación en Finanzas:** Predecir la dirección del precio (sube/baja/estable), señales de compra/venta, riesgo crediticio.
        * **Ventajas (del modelo específico, ej. RF):** Buena precisión, robusto al sobreajuste, maneja bien características heterogéneas, puede estimar la importancia de las variables.
        * **Desventajas (del modelo específico, ej. RF):** Puede ser más lento de entrenar que modelos simples, menos interpretable que un solo árbol.

https://careers.minsait.com/Minsait/job/Inteligencia-Artificial-Perfil-Junior/978243255/
https://es.trabajo.org/


---
