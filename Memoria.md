# Proyecto: Análisis y Predicción de ETFs de EEUU

**Autor/es:** Ivan López Tomàs y Nelson William Morales 

**Repositorio:** https://github.com/nwmorales/ETF_Predictions

---

## 1. Introducción

Este proyecto se centra en el análisis de Fondos Cotizados (ETFs) relevantes del mercado estadounidense. El objetivo principal es identificar los ETFs con mejor rendimiento histórico reciente y utilizar sus datos para construir modelos predictivos que intenten anticipar futuros movimientos del mercado. La finalidad última es explorar la viabilidad de utilizar estos modelos como apoyo en la toma de decisiones de inversión.

El flujo de trabajo abarca desde la obtención y limpieza de datos históricos de ETFs hasta el entrenamiento y evaluación de modelos de Machine Learning para la predicción de precios o tendencias.

---

## 2. Motivación

Los mercados financieros, y en particular los ETFs, ofrecen oportunidades de inversión, pero su comportamiento es complejo y volátil. Predecir sus movimientos es un desafío constante. Este proyecto surge de la necesidad de:

*   Aplicar técnicas de ciencia de datos para entender mejor el comportamiento de los ETFs.
*   Explorar la capacidad predictiva de modelos de Machine Learning sobre datos financieros históricos.
*   Desarrollar una metodología sistemática para la selección de activos (basada en rendimiento pasado) y la posterior modelización.
*   Generar herramientas o insights que *potencialmente* podrían ayudar a fundamentar estrategias de inversión (con las debidas precauciones).

---

## 3. Datos

### 3.1. Fuente de Datos

Los datos históricos de precios (como Apertura, Máximo, Mínimo, Cierre, Cierre Ajustado, Volumen) para los ETFs se obtuvieron de Kaggle y posteriormente se amplió con la API de Yahoo Finance. Se recopilaron datos para una amplia selección de ETFs importantes del mercado estadounidense.

### 3.2. Descripción de los Datos

El dataset inicial contiene información de series temporales para múltiples ETFs. Las características principales por ETF incluyen:

*   `Date`: Fecha de la cotización.
*   `Open`: Precio de apertura.
*   `High`: Precio máximo del día.
*   `Low`: Precio mínimo del día.
*   `Close`: Precio de cierre.
*   `Adj Close`: Precio de cierre ajustado (considerando dividendos y splits).
*   `Volume`: Volumen de acciones negociadas.
*   `Ticker`: Símbolo identificador del ETF.

### 3.3. Procesamiento y Limpieza

Se aplicaron los siguientes pasos de preprocesamiento:

1.  **Manejo de Valores Faltantes:** [Describe cómo se trataron: Ej. eliminación de filas/columnas, imputación con media/mediana/valor anterior, etc.].
2.  **Verificación de Tipos de Datos:** Asegurar que las fechas sean `datetime` y los valores numéricos sean `float` o `int`.
3.  **Consistencia de Datos:** [Si se realizó alguna otra verificación, ej. eliminar días sin negociación, outliers, etc.].
4.  **Cálculo de Rentabilidad:** Se calculó la rentabilidad histórica (Ej. retorno acumulado, CAGR, Sharpe Ratio, etc.) para cada ETF durante un período específico [Especifica el período, ej. "el último año", "los últimos 3 años"] para poder realizar el filtrado.

### 3.4. Filtrado de ETFs

Con base en la rentabilidad histórica calculada en el paso anterior, se seleccionaron los **20 ETFs con mayor rendimiento**. Este subconjunto de ETFs fue el utilizado para la fase de modelado predictivo.

**Nota Importante:** La selección basada en rendimiento pasado *no garantiza* rendimientos futuros similares. Este es un criterio de filtrado para enfocar el análisis, pero conlleva el riesgo inherente de que los ETFs seleccionados no mantengan su rendimiento superior.

---

## 4. Metodología

### 4.1. Metodología de Minería de Datos 

Para este proyecto se utilizará la metodología **CRISP-DM** (Cross-Industry Standard Process for Data Mining), ya que es una de las más utilizadas en ciencia de datos por su enfoque estructurado y flexible. Se eligió porque permite organizar todo el proceso de forma lógica, desde entender el problema hasta aplicar y evaluar modelos.

### 4.2. Tecnologías Utilizadas

*   **Lenguaje:** Python ([Versión, ej. 3.9+])
*   **Librerías Principales:**
    *   `Pandas`: Manipulación y análisis de datos.
    *   `NumPy`: Operaciones numéricas.
    *   `Scikit-learn`: Modelos de Machine Learning, preprocesamiento y evaluación.
    *   `Matplotlib` / `Seaborn`: Visualización de datos.
    *   [Otras librerías usadas: Ej. `yfinance` para datos, `TensorFlow`/`Keras`/`PyTorch` si usaste Deep Learning, `Statsmodels` si usaste modelos estadísticos como ARIMA, etc.]
*   **Entorno:** Google Colab
*   **Docker**
*   **Apache Nifi**
*   **Apache Hadoop** 
*   **Apache Cassandra**
*   **Orange Datamining**
  

### 4.3. Feature Engineering (Ingeniería de Características)

Para mejorar la capacidad predictiva de los modelos, se crearon características adicionales a partir de los datos históricos, tales como:

*   Medias móviles (simples o exponenciales).
*   Indicadores técnicos (RSI, MACD, Bandas de Bollinger, etc.).
*   Variables de Lag (valores de días anteriores).
*   Diferencias de precios o retornos diarios/semanales.
*   [Cualquier otra característica que hayas creado].

### 4.4. Modelos de Predicción

Se experimentó con los siguientes modelos de Machine Learning para predecir [Especifica qué se predice: Ej. el precio de cierre del día siguiente, la dirección del movimiento (sube/baja), un rango de precios]:

*   [Modelo 1: Ej. Regresión Lineal, ARIMA]
*   [Modelo 2: Ej. Random Forest Regressor/Classifier]
*   [Modelo 3: Ej. Gradient Boosting (XGBoost, LightGBM)]
*   [Modelo 4: Ej. Redes Neuronales Recurrentes (LSTM, GRU) - si aplica]
*   [Otros modelos probados]

Para cada modelo, se realizó una división de los datos en conjuntos de entrenamiento y prueba (y posiblemente validación), respetando el orden temporal para evitar *data leakage*. Se llevó a cabo [Menciona si hiciste optimización de hiperparámetros, ej. GridSearchCV, RandomizedSearchCV].

### 4.5. Evaluación

Los modelos se evaluaron utilizando las siguientes métricas:

*   **Para Regresión (predicción de precio):**
    *   Error Absoluto Medio (MAE)
    *   Error Cuadrático Medio (MSE)
    *   Raíz del Error Cuadrático Medio (RMSE)
    *   Coeficiente de Determinación (R²)
*   **Para Clasificación (predicción de dirección):**
    *   Accuracy (Exactitud)
    *   Precision, Recall, F1-Score
    *   Matriz de Confusión
    *   Curva ROC / AUC
*   [Otras métricas relevantes, quizás financieras como Profit/Loss simulado]

---

## 5. Resultados

En esta sección se resumen los hallazgos principales:

*   [Describe brevemente el rendimiento general de los modelos. ¿Fueron capaces de predecir con cierta precisión?]
*   [¿Qué modelo(s) funcionó/funcionaron mejor según las métricas de evaluación?]
*   [Incluye aquí enlaces a Notebooks con análisis detallados, gráficos clave (puedes subir imágenes al repo y enlazarlas), o tablas resumen.]
    *   Ejemplo: `![Comparativa de RMSE](ruta/a/tu/imagen_rmse.png)`
*   [Algún insight interesante descubierto durante el análisis o modelado.]

**Ejemplo:**
"El modelo LSTM mostró el RMSE más bajo en la predicción del precio de cierre a 1 día vista para la mayoría de los ETFs analizados, aunque el modelo Random Forest fue más robusto para predecir la dirección del movimiento (subida/bajada) con una Accuracy del X% en el conjunto de prueba."

---

## 6. Discusión y Limitaciones

*   **Complejidad del Mercado:** La predicción de mercados financieros es intrínsecamente difícil debido a su naturaleza caótica y la influencia de factores externos no capturados en los datos históricos (noticias, eventos geopolíticos, sentimiento del mercado, etc.).
*   **Selección Basada en Rendimiento Pasado:** Como se mencionó, filtrar por los ETFs más rentables históricamente introduce un sesgo. El rendimiento pasado no es garantía de resultados futuros.
*   **Overfitting:** Existe el riesgo de que los modelos se ajusten demasiado a los datos de entrenamiento y no generalicen bien a datos nuevos (futuros). Se tomaron medidas como [Cross-Validation, Regularización] para mitigarlo, pero el riesgo persiste.
*   **Calidad y Horizonte de Datos:** La precisión de los modelos depende fuertemente de la calidad y la cantidad de datos históricos disponibles. Períodos más largos o datos más granulares podrían mejorar (o cambiar) los resultados.
*   **Modelo Simplificado:** Los modelos actuales no incorporan [Menciona factores no incluidos: Ej. análisis de sentimiento de noticias, datos macroeconómicos, correlaciones entre ETFs, etc.].

**IMPORTANTE:** Este proyecto es de carácter académico/exploratorio. **Los resultados y modelos presentados NO constituyen asesoramiento financiero.** Cualquier decisión de inversión basada en este trabajo se realiza bajo la total responsabilidad del usuario.

---

## 7. Trabajo Futuro

Posibles líneas de mejora y expansión del proyecto:

*   Incorporar más fuentes de datos (noticias financieras, sentimiento de redes sociales, indicadores macroeconómicos).
*   Probar arquitecturas de modelos más avanzadas (Transformers, modelos híbridos).
*   Implementar estrategias de backtesting más rigurosas para simular el rendimiento de inversión de forma realista.
*   Desarrollar un pipeline automatizado para la re-entrenamiento periódico de los modelos.
*   Explorar técnicas de optimización de portafolios basadas en las predicciones.
*   Analizar el impacto de diferentes horizontes temporales de predicción.

---

## 8. Instalación y Uso

1.  **Clonar el repositorio:**
    ```bash
    git clone [Link a tu repositorio de GitHub]
    cd [Nombre de la carpeta del proyecto]
    ```

2.  **Crear un entorno virtual (recomendado):**
    ```bash
    python -m venv env
    # En Windows
    .\env\Scripts\activate
    # En macOS/Linux
    source env/bin/activate
    ```

3.  **Instalar dependencias:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Asegúrate de tener un archivo `requirements.txt` con todas las librerías necesarias. Puedes generarlo con `pip freeze > requirements.txt`)*

4.  **Ejecutar el proyecto:**
    *   [Explica cómo ejecutar los scripts o notebooks principales. Ej: "Abrir y ejecutar los notebooks en orden: `01_data_acquisition.ipynb`, `02_data_cleaning.ipynb`, `03_feature_engineering.ipynb`, `04_modeling.ipynb`, `05_evaluation.ipynb`"]
    *   [O si tienes un script principal: `python main.py --opcion`]

