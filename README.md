# Mobility & Economy Analysis 2024

Este repositorio contiene el análisis de movilidad urbana e indicadores económicos realizado con datos de TomTom Traffic y OECD para el año 2024.

El dataset final (`ladb_mobility_economy_2024_clean.csv`) integra datos de tráfico e indicadores económicos de 15 ciudades latinoamericanas, permitiendo explorar la relación entre congestión vehicular y productividad urbana.

## 📂 Contenido del repositorio

- `notebooks/mobility_economy_analysis.ipynb`  
  → Notebook principal con carga, limpieza, EDA, visualizaciones y conclusiones.

- `ladb_mobility_economy_2024_clean.csv`  
  → Dataset final exportado con 15 ciudades y 15 columnas limpias.

## ▶ Cómo abrir el notebook en Google Colab

Haz clic en el siguiente botón:

[![Open In_Colab] https://colab.research.google.com/github/imjesusgarcia/mobility_economy_project_student/blob/main/S5_ladb_mobility_economy_project_student.ipynb 

O:

1. Abre el archivo `.ipynb` en GitHub  
2. Haz clic en **Open in Colab**

## 📘 Cómo reproducir el análisis

1. Abre `notebooks/mobility_economy_analysis.ipynb`
2. Ejecuta las celdas en orden
3. El notebook carga los datasets desde:
   - `/datasets/tomtom_traffic.csv`
   - `/datasets/oecd_city_economy.csv`

## 🧠 Objetivo del análisis

- Explorar la relación entre congestión vehicular y PIB per cápita en ciudades latinoamericanas
- Integrar y limpiar datos de dos fuentes heterogéneas (TomTom + OECD)
- Estandarizar columnas, tipos de datos y formatos numéricos
- Calcular promedios anuales de tráfico por ciudad para análisis consolidado
- Generar visualizaciones comparativas entre movilidad y economía
- Identificar ciudades prioritarias para inversión en infraestructura de transporte

## 📊 Datasets utilizados

| Dataset | Fuente | Registros | Descripción |
|---|---|---|---|
| `tomtom_traffic.csv` | TomTom | 1,004,464 | Índices de tráfico por ciudad y fecha |
| `oecd_city_economy.csv` | OECD | 30 | PIB per cápita, desempleo, PM2.5 y población |

## 🌎 Ciudades y países incluidos

7 países: Brasil, Colombia, Argentina, Perú, México, Uruguay y Chile  
15 ciudades analizadas en el año 2024.

## 🔑 Hallazgos principales

- **Bogotá** presenta el mayor ratio congestión/productividad, posicionándose como ciudad prioritaria para inversión en infraestructura vial.
- No se observa correlación lineal fuerte entre PIB per cápita y congestión: algunas ciudades con alta congestión mantienen PIB elevado, sugiriendo que la congestión puede ser consecuencia del crecimiento económico.
- La distribución de `JamsDelay` muestra valores atípicos significativos (mediana ~250 min vs. promedio ~630 min), indicando que pocas ciudades con congestión extrema sesgan la media general.

## 🛠 Tecnologías utilizadas

- Python 3
- pandas · NumPy · Matplotlib · Seaborn
