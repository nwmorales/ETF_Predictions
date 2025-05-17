# Análisis y Predicción de ETFs de EEUU con IA y Big Data

## Descripción General

Este proyecto se enfoca en el diseño, implementación y evaluación de un sistema basado en tecnologías Big Data e Inteligencia Artificial para el análisis y la predicción del comportamiento de Fondos Cotizados en Bolsa (ETFs) del mercado estadounidense. El objetivo es establecer un pipeline completo para la ingesta, procesamiento, almacenamiento y posterior modelado de datos históricos de ETFs.

La solución integra Docker y Docker Compose para la gestión y orquestación de un entorno contenerizado que incluye Apache NiFi para el flujo y transformación de datos, Apache Cassandra como base de datos NoSQL para acceso rápido, y Apache Hadoop (HDFS) para el almacenamiento masivo de datos históricos. El análisis exploratorio de datos (EDA), el desarrollo de modelos predictivos (incluyendo Regresión Lineal, Prophet, Redes Neuronales y modelos de Clasificación) y la visualización se realizan utilizando Python (en Google Colab), Orange Datamining y Microsoft Power BI.

## Tabla de Contenidos
* [Descripción General](#descripción-general)
* [Arquitectura del Sistema](#arquitectura-del-sistema)
* [Tecnologías Utilizadas](#tecnologías-utilizadas)
* [Fuentes de Datos](#fuentes-de-datos)
* [Estructura del Proyecto](#estructura-del-proyecto)
* [Prerrequisitos](#prerrequisitos)
* [Instalación y Configuración](#instalación-y-configuración)
* [Uso del Proyecto](#uso-del-proyecto)
* [Resultados Clave (Resumen)](#resultados-clave-resumen)
* [Trabajos Futuros](#trabajos-futuros)
* [Licencia](#licencia)
* [Agradecimientos](#agradecimientos)

## Arquitectura del Sistema

La arquitectura de la solución está diseñada para manejar el ciclo de vida completo de los datos de ETFs. Un flujo de datos orquestado por Apache NiFi ingesta datos de fuentes externas, los transforma (ej. a formato Avro) y los distribuye a Apache HDFS para almacenamiento histórico y a Apache Cassandra para acceso operacional rápido. Estos datos luego alimentan los procesos de análisis y modelado. Todos los componentes de la infraestructura se ejecutan en contenedores Docker.

## Tecnologías Utilizadas

* **Lenguaje de Programación (Modelado y Scripts):** Python
* **Análisis de Datos y ML (Python):** Pandas, NumPy, Scikit-learn, Prophet, [Especificar librerías de Redes Neuronales, ej: TensorFlow/Keras]
* **Contenerización y Orquestación:** Docker, Docker Compose
* **Flujo de Datos (ETL):** Apache NiFi (versión 1.28.0)
* **Almacenamiento Big Data:**
    * Apache Hadoop (HDFS) (versión 3.2.1, imagen bde2020/hadoop-namenode/datanode)
    * Apache Cassandra (versión 4.1)
* **Visualización de Datos:** Microsoft Power BI
* **Minería de Datos Visual:** Orange Datamining
* **Entorno de Desarrollo (Notebooks):** Google Colab, Jupyter Notebooks (si aplica)

## Fuentes de Datos

* **Kaggle Dataset:** "Mutual Funds and ETFs" por Stefano Leone ([https://www.kaggle.com/datasets/stefanoleone992/mutual-funds-and-etfs](https://www.kaggle.com/datasets/stefanoleone992/mutual-funds-and-etfs)).
    * Archivo específico utilizado: ETF prices.csv
    * Contenido: Precios históricos diarios (OHLCV) y volumen para una amplia gama de ETFs de EEUU, cubriendo desde el 29 de enero de 1993 hasta el 31 de Noviembre de 2021.
* **Yahoo Finance API:**
    * [**COMPLETAR POR EL USUARIO:** Propósito de uso (ej. "para obtener datos más recientes no cubiertos por el dataset de Kaggle" o "para ETFs específicos"). Especificar la librería de Python si se usó, ej. `yfinance`].

## Estructura del Proyecto
├── BigData/
│   ├── Docker/
│   │   └── docker-compose.yml
│   ├── Hadoop/
│   │   └── core-site.xml
│   ├── Nifi/
│   │   ├── ConfiguracionNifi.ipynb  # Notebook con guía/pasos para configurar Controller Services en NiFi
│   │   └── ETF_Final (1).xml        # Plantilla del flujo de NiFi
│   └── Python/                      # Scripts de Python auxiliares o de modelado (a detallar)
├── Datasets/
│   ├── ETF_cohortes.csv
│   ├── ETFs.csv
│   ├── top20_ETFs.csv
│   └── ETF_cohortes_final_preprocesado.csv # Archivo de entrada principal para NiFi
├── Exploracion de datos/
│   ├── PowerBI/
│   │   └── ETF.pbix
│   └── OrangeDatamining/
│       └── ETF_Orange_Datamining.ows
├── Modelado/                          # Notebooks o scripts para el desarrollo y entrenamiento de modelos
│   └── [Ej: 1_Modelo_RegresionLineal.ipynb]
│   └── [Ej: 2_Modelo_Prophet.ipynb]
│   └── [Ej: 3_Modelo_RedNeuronal.ipynb]
│   └── [Ej: 4_Modelos_Clasificacion.ipynb]
├── Proyecto final/                    # (Contenido a definir por el usuario, ej: entregables finales)
├── memoria.doc                        # Documento de la memoria del proyecto
└── README.md                          # Este archivo

## Prerrequisitos

* Docker Desktop instalado y en ejecución.
* Docker Compose (generalmente incluido con Docker Desktop).
* Git (para clonar el repositorio).
* Conexión a internet (para descargar imágenes Docker si es la primera vez).
* Power BI Desktop instalado
* Orange Datamining instalado

## Instalación y Configuración

1.  **Clonar el Repositorio:**

2.  **Preparar Archivos de Configuración y Datos de Entrada para NiFi:**
    * Asegúrate de que el archivo de configuración de Hadoop `core-site.xml` esté presente en la ruta `BigData/Hadoop/core-site.xml`. Su contenido debe ser:
        ```xml
        <configuration>
            <property>
                <name>fs.defaultFS</name>
                <value>hdfs://namenode:9000</value>
            </property>
        </configuration>
        ```
    * **Importante para NiFi:** El archivo `docker-compose.yml` (ubicado en `BigData/Docker/`) está configurado para mapear un volumen desde el host a NiFi. Para que NiFi ingeste los datos, debes:
        * Crear una carpeta en tu máquina host en la misma ubicación que tu archivo `docker-compose.yml`, por ejemplo: `BigData/Docker/nifi_data_input/`.
        * **Copiar** el archivo `Datasets/ETF_cohortes_final_preprocesado.csv` dentro de esta carpeta `BigData/Docker/nifi_data_input/`.
        * **Verifica el `docker-compose.yml`:** Asegúrate de que el volumen para el servicio de NiFi mapee correctamente esta carpeta del host a `/data_in` dentro del contenedor de NiFi. Por ejemplo, en tu `docker-compose.yml` para el servicio `nifi`, la sección de volúmenes debería tener algo como:

3.  **Levantar el Entorno Docker:**
    Navega al directorio donde se encuentra tu `docker-compose.yml` (`BigData/Docker/`) y ejecuta:
    ```bash
    docker-compose up -d
    ```
    Esto iniciará todos los servicios (NiFi, HDFS NameNode, HDFS DataNodes, Cassandra) en segundo plano. La primera vez puede tardar unos minutos mientras se descargan las imágenes. Espera a que todos los servicios indiquen que están "healthy" o "started" en la salida de Docker o usando `docker-compose ps`.

4.  **Configurar Apache NiFi (Controller Services e Importar Plantilla):**
    * Accede a la interfaz web de NiFi: `https://localhost:8443/nifi` (o el puerto que hayas configurado).
    * **Configuración Manual de Controller Services:** Antes de importar la plantilla del flujo, es crucial configurar manualmente los Controller Services que esta utiliza. Consulta el notebook `BigData/Nifi/ConfiguracionNifi.ipynb` para obtener una guía detallada de los Controller Services a crear (como `CSVReader`, `AvroRecordSetWriter`, `CassandraSessionProvider`, `AvroReader`) y sus parámetros específicos. Habilítalos una vez configurados.
    * **Importar Plantilla de Flujo:** Sube la plantilla `BigData/Nifi/ETF_Final (1).xml` a través de la interfaz de NiFi (usando el menú de Operate Palette -> Upload Template) e instánciala en el lienzo.
    * Verifica que los procesadores en el flujo estén correctamente configurados y enlazados a los Controller Services que creaste. Inicia los procesadores o el flujo completo.

5.  **Acceder a los Servicios (para verificación):**
    * **Apache NiFi UI:** `https://localhost:8443/nifi`
    * **HDFS NameNode UI:** `http://localhost:9870`
    * **Cassandra (via cqlsh):**
        ```bash
        docker-compose -f BigData/Docker/docker-compose.yml exec cassandra cqlsh 
        ```
        *(Ajusta la ruta al yml si ejecutas desde la raíz del proyecto)*

## Uso del Proyecto

1.  **Ingesta de Datos:**
    * Una vez NiFi esté configurado y el flujo iniciado, los datos del archivo `ETF_cohortes_final_preprocesado.csv` (ubicado según las instrucciones de instalación) serán automáticamente ingeridos, transformados a Avro y cargados en HDFS y Cassandra.
    * Monitoriza el proceso a través de la UI de NiFi.

2.  **Verificación de Datos Almacenados:**
    * **HDFS:**
        ```bash
        docker-compose -f BigData/Docker/docker-compose.yml exec namenode hdfs dfs -ls /etf_project/data_avro/
        ```
    * **Cassandra:**
        ```cql
        // Desde cqlsh conectado al contenedor de cassandra
        USE etf_data;
        SELECT * FROM etf_quotes_final LIMIT 5; -- (Usa el nombre real de tu tabla)
        ```

3.  **Análisis Exploratorio de Datos (EDA) y Modelado:**
    * [**COMPLETAR POR EL USUARIO/COMPAÑERO:** Describe brevemente cómo ejecutar los notebooks o scripts de EDA y modelado. Indica la ubicación de los notebooks principales (ej. en la carpeta `Modelado/` o `Exploracion de datos/`). Ej: "Abrir el notebook `Modelado/entrenamiento_modelos.ipynb` en Google Colab o un entorno Jupyter local y ejecutar las celdas secuencialmente..."]
    * [Menciona si los notebooks se conectan a Cassandra o leen datos exportados].

4.  **Visualización (Power BI):**
    * Abre el archivo `Exploracion de datos/PowerBI/ETF.pbix` con Microsoft Power BI Desktop.

5.  **Minería de Datos Visual (Orange):**
    * Abre el archivo de flujo de trabajo `Exploracion de datos/OrangeDatamining/ETF_Orange_Datamining.ows` con Orange Datamining.

## Resultados Clave (Resumen)
* La arquitectura Big Data fue implementada exitosamente, permitiendo el flujo de datos desde la ingesta hasta el almacenamiento distribuido.
* [**COMPLETAR POR EL USUARIO/COMPAÑERO:** Añadir 1-2 resultados clave del análisis o de los modelos predictivos una vez disponibles. Ej: "El modelo X alcanzó una métrica Y de Z."].
* *(Para más detalles, consultar la memoria completa del proyecto (`memoria.doc`)).*

## Trabajos Futuros
* [**COMPLETAR POR EL USUARIO:** Idea 1, ej: Mejorar la ingesta de datos para que sea en tiempo real desde la API de Yahoo Finance].
* [**COMPLETAR POR EL USUARIO:** Idea 2, ej: Probar arquitecturas de Redes Neuronales más avanzadas como Transformers].
* [**COMPLETAR POR EL USUARIO/COMPAÑERO:** Idea 3, ej: Desarrollar un sistema de backtesting para las predicciones].

## Licencia
Distribuido bajo la Licencia MIT. Ver `LICENSE` para más información.
*(**Instrucción para ti:** Crea un archivo `LICENSE` en la raíz de tu proyecto y pega el texto de la licencia MIT si decides usarla. Puedes encontrarlo fácilmente online buscando "MIT License text").*

## Agradecimientos
* A Stefano Leone por el dataset "Mutual Funds and ETFs" disponible en Kaggle.
* A las comunidades de desarrollo de Apache NiFi, Hadoop, Cassandra, Docker, Python, Orange y Power BI.
* [**COMPLETAR POR EL USUARIO:** Agradecimientos a profesores, tutores, universidad, etc.].
