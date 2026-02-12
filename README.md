# Pipeline de Predicción de Demanda en Retail (End-to-End)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![Skforecast](https://img.shields.io/badge/Forecasting-Skforecast-orange)
![Machine Learning](https://img.shields.io/badge/Model-Gradient%20Boosting-green)
![Status](https://img.shields.io/badge/Status-TFG%20Completado-lightgrey)

Este repositorio contiene el código fuente y la documentación técnica de un **Trabajo de Fin de Grado (TFG)** centrado en la predicción de series temporales para el sector retail.

El proyecto implementa un flujo de trabajo comparativo robusto que evalúa tres enfoques distintos: un **Baseline Ingenuo (Media Móvil)**, modelos estadísticos clásicos (**ARIMA/SARIMAX**) y algoritmos modernos de Machine Learning Supervisado (**Gradient Boosting**).

## Objetivo del Proyecto

Optimizar la precisión del pronóstico de ventas a nivel de tienda y producto para mejorar la planificación de inventario, minimizar costes de almacenamiento y evitar roturas de stock.

## Metodología y Arquitectura

El desarrollo se estructura en un único *pipeline* secuencial (`Pipeline_Prediccion_Demanda.ipynb`) que abarca las siguientes fases:

### 1. Análisis Exploratorio de Datos (EDA)
Estudio exhaustivo de la naturaleza de la serie temporal:
* **Descomposición:** Análisis de componentes de Tendencia, Estacionalidad y Residuo.
* **Tests de Estacionariedad:** Aplicación de pruebas (Dickey-Fuller) para validar la estabilidad de la serie.
* **Autocorrelación:** Gráficos ACF y PACF para identificar patrones temporales.

### 2. Baseline y Modelado Estadístico
Para validar la eficacia del Machine Learning, establecemos dos puntos de referencia:
* **Media Móvil (Baseline):** Modelo simple de ventana deslizante para establecer el error mínimo aceptable.
* **ARIMA / SARIMAX (Benchmark):** Implementación de modelos econométricos clásicos. Se utiliza `pmdarima` para la selección automática de hiperparámetros `(p,d,q)` basada en la optimización del criterio AIC.

### 3. Machine Learning Avanzado (Skforecast)
Transformación del problema de series temporales en un problema de regresión supervisada:
* **Ingeniería de Features:** Creación de variables exógenas, retardos (*lags*) y ventanas móviles (*rolling statistics*).
* **Modelo:** Entrenamiento de un Regresor de **Gradient Boosting** (LightGBM/XGBoost) capaz de capturar relaciones no lineales complejas.
* **Validación:** Uso de `ForecasterRecursive` para predicciones *multi-step*.

## Stack Tecnológico

* **Lenguaje Principal:** Python 3.x
* **Orquestación de Forecasting:** `skforecast`.
* **Modelado Estadístico:** `pmdarima`, `statsmodels`.
* **Machine Learning:** `scikit-learn`, `lightgbm`.
* **Manipulación de Datos:** `pandas`, `numpy`.
* **Visualización:** `matplotlib`, `seaborn`, `plotly`.

## Estructura del Repositorio

```text
├── data/
│   └── demanda.csv                  # Dataset histórico transaccional
├── Pipeline_Prediccion_Demanda.ipynb # Notebook Maestro (Todo el análisis)
├── requirements.txt                 # Dependencias y versiones exactas
└── README.md                        # Documentación técnica
