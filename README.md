Proyecto de Segmentación Estratégica de Clientes B2B
Descripción del Proyecto
Este repositorio contiene el código y la documentación del proyecto final integrador para la Diplomatura en Data Science. El objetivo del proyecto es desarrollar un modelo de aprendizaje no supervisado para segmentar la base de clientes B2B de una empresa de medios, con el fin de optimizar las estrategias de marketing, ventas y gestión de cuentas.
Se aplicó la metodología CRISP-DM para guiar el proyecto, desde la comprensión del problema de negocio hasta la evaluación final de los modelos. El análisis se realiza sobre un dataset anonimizado a nivel de campaña, que abarca desde enero de 2023 hasta diciembre de 2025.
Metodología y Pasos del Análisis
El análisis se llevó a cabo en el notebook de Python (Análisis_y_Segmentación_de_Clientes.ipynb) y siguió los siguientes pasos clave:
Preparación de Datos: Carga del dataset, limpieza de nombres de columnas, manejo inicial de valores nulos y conversión de tipos de datos. Se crea la variable id_cliente (Agencia-País) como unidad de análisis principal.
Ingeniería de Variables (Feature Engineering): Creación de 8 métricas de negocio para construir un perfil 360° de cada cliente a partir de los datos transaccionales. Las variables creadas incluyen:
AntiguedadRelacion
AvgInversionPorCampana
DiversidadMarcas y DiversidadFormatos
TasaComisionPromedio (calculada a partir de los rebates)
VolumenInversion_12M y MargenTotal_12M
MargenPorMarca (ratio de eficiencia clave)
Segmentación Estratégica: Separación crucial de los clientes en Activos (con inversión en los últimos 12 meses) e Inactivos, para enfocar el análisis de clustering en el grupo de negocio relevante.
Análisis Exploratorio de Datos (EDA): Visualización de las distribuciones (histogramas), identificación de outliers (boxplots) y análisis de relaciones (matriz de correlación) sobre el subgrupo de clientes activos.
Preprocesamiento para Modelado:
Selección de Variables: Eliminación de variables redundantes (AvgMargen, MargenTotal_12M) identificadas en el EDA.
Transformación Logarítmica: Aplicación de np.log1p para manejar la asimetría y el impacto de los outliers.
Escalado de Datos: Estandarización de todas las variables con StandardScaler para preparar los datos para los algoritdeos de clustering.
Modelado y Comparación:
K-Means: Implementación y ajuste de hiperparámetros (n_init=25), y selección de k=4 clusters mediante el Método del Codo y el Coeficiente de Silueta.
DBSCAN: Implementación y ajuste de hiperparámetros (min_samples y eps) para identificar clusters basados en densidad y detectar clientes atípicos ("ruido").
Gaussian Mixture Models (GMM): Implementación y optimización del número de componentes mediante el Criterio de Información Bayesiano (BIC) y ajuste del hiperparámetro covariance_type.
Evaluación Final: Comparación cuantitativa de los tres modelos utilizando métricas estándar (Coeficiente de Silueta, Calinski-Harabasz, Davies-Bouldin) para seleccionar el modelo óptimo.
Interpretación de Resultados: Perfilado y descripción detallada de los segmentos de negocio encontrados a partir del modelo K-Means, incluyendo visualizaciones comparativas.
Cómo Ejecutar el Código
Para replicar el análisis, sigue estos pasos:
1. Prerrequisitos
Asegúrate de tener acceso a un entorno de Python 3. El código fue desarrollado en Google Colab. Las librerías necesarias son:
pandas
numpy
matplotlib
seaborn
scikit-learn


Estas librerías vienen preinstaladas en Google Colab, por lo que no se requiere instalación adicional si se utiliza ese entorno.
2. Configuración del Entorno
Clona o descarga este repositorio en tu máquina local.
Sube tu archivo de datos dataset_clientes.csv a tu Google Drive. 
Abre el notebook Análisis_y_Segmentación_de_Clientes.ipynb en Google Colab.
Verifica la ruta del archivo: Dentro del notebook, en el PASO 1, asegúrate de que la variable file_path apunte a la ubicación correcta de tu Google Drive donde guardaste el dataset.
