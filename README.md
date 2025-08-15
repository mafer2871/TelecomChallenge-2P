---
# **Telecom X Parte 2: Predicción de Cancelación de Clientes (Churn)**


## 📉 Contexto del Problema 

La cancelación de clientes (churn) representa una pérdida significativa de ingresos y una amenaza para el crecimiento de la empresa. Identificar y retener a los clientes en riesgo es una prioridad estratégica. Este proyecto se enfoca en analizar los datos históricos para construir una herramienta predictiva que anticipe el abandono de clientes, permitiendo a la empresa actuar de manera proactiva.

---

## 📂 Estructura del Proyecto 

El repositorio está organizado de la siguiente manera para facilitar su comprensión y replicabilidad:
telecomX2p.ipynb: Archivo principal de Google Colab que contiene el código completo para el preprocesamiento de datos, el modelado, la evaluación de métricas y la generación de gráficos.
resultados/: Carpeta que almacena los productos del análisis, incluyendo:
graficas/: Visualizaciones de la matriz de confusión, curvas ROC e importancia de las variables.
metricas/: Tablas CSV con las métricas de rendimiento e importancia de las variables para cada modelo.
modelos/: Los modelos de Machine Learning entrenados y guardados en formato .pkl.
Uso_modelo.ipynb:  Archivo de Google Colab con el código para uso del modelo con otro conjunto de datos.

---

## ⚡ Cómo Ejecutar el Código 
Acceder al Notebook de Google Colab: Abre el archivo telecomx.ipynb en Google Colab.
Ejecutar las Celdas: Ejecuta las celdas de código secuencialmente en el notebook. Los resultados del análisis y las visualizaciones se mostrarán directamente en el notebook.

3. Datos del Proyecto 💾

Los datos utilizados para este análisis son el resultado de un proceso de ETL previo. Se toman de un archivo CSV disponible públicamente en el siguiente enlace:
Fuente de Datos: https://raw.githubusercontent.com/mafer2871/ChallegeTelecomX/main/Datos/cancelaciones.csv

---

## 🔍 Análisis Exploratorio y Hallazgos Clave 

El análisis de los datos reveló patrones críticos que actúan como señales de alerta temprana:
Contratos Mes a Mes: Los clientes con este tipo de contrato son, por mucho, el segmento de mayor riesgo.
Antigüedad en la Empresa: Los clientes en sus primeros meses son los más propensos a cancelar.
Servicio de Fibra Óptica: La contratación de este servicio está fuertemente correlacionada con una mayor tasa de abandono, sugiriendo problemas de calidad o satisfacción.
Pagos Elevados: Los clientes con altos cargos mensuales y que utilizan cheques electrónicos tienen un mayor riesgo de churn.

---

## 🛠️ Metodología de Modelado 

Se implementó un pipeline de ciencia de datos para garantizar la consistencia y fiabilidad del modelo. Este proceso incluyó:
Preprocesamiento de Datos: Transformación de variables categóricas y escalado de variables numéricas.
Manejo del Desbalance de Clases: Uso de SMOTE para equilibrar el conjunto de datos de entrenamiento, ya que la clase de clientes que cancelaron era minoritaria.
Entrenamiento y Optimización: Se evaluaron tres modelos de clasificación, optimizando sus hiperparámetros para encontrar el mejor rendimiento.

---

## 📈 Resultados y Métricas Clave 

Tras la optimización, se obtuvieron las siguientes métricas para cada modelo. Las métricas de Precision y Recall se consideran las más importantes para este problema.
| Modelo | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Regresión Logística** | 0.744 | 0.512 |   0.805   | 0.626 |   0.843   |
| **Random Forest** | **0.772** | **0.555** | 0.719 | **0.626** | 0.841 |
| **XGBoost** | 0.770 | 0.569 | 0.563 | 0.566 | 0.814 |

Conclusión de los Resultados: El modelo de Random Forest es la mejor opción, ya que presenta la mayor precisión y un buen Recall, permitiendole identificar de manera fiable a un alto porcentaje de clientes en riesgo sin generar un exceso de falsas alarmas, lo cual es ideal para una estrategia de retención eficiente.

---

## 💡 Recomendaciones Estratégicas 

Basadas en los hallazgos de los modelos, se proponen las siguientes acciones concretas:

- Fidelización Temprana: Centrar los esfuerzos en los clientes con contratos mes a mes en sus primeros 3-6 meses. Utilizar el modelo para identificarlos y ofrecerles incentivos personalizados (descuentos, upgrades) para que se cambien a un contrato de un año o más.
- Mejora del Servicio de Fibra Óptica: Investigar las causas subyacentes de la insatisfacción de los clientes de fibra óptica. Fortalecer el soporte técnico para este segmento y considerar un programa de monitoreo proactivo para detectar problemas antes de que el cliente los reporte.
- Optimización de Pagos: Ofrecer incentivos a los clientes que usan cheques electrónicos para que cambien a métodos de pago más convenientes y automáticos, lo que puede aumentar la lealtad.

---

## 🚀 Uso del Modelo 

El modelo final (Random Forest) ha sido guardado en el archivo resultados/modelos/mejor_modelo.pkl. Puede ser cargado y utilizado fácilmente para predecir el riesgo de churn en nuevos datos de clientes, el código para uso se encuentra en el archivo uso_modelo.ipynb de este repositorio.

---

## 🧑‍💻 Autoría y Tecnologías 

Autor: María Fernanda Rodríguez
Tecnologías Utilizadas: Python, pandas, numpy, scikit-learn, xgboost, imblearn, matplotlib, seaborn.
