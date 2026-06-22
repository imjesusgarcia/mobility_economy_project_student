# Proyecto 5 — Movilidad Urbana y Productividad Económica en Latinoamérica

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/imjesusgarcia/Student-Version-Project-LADB/blob/main/S5_ladb_mobility_economy_project_student__1_.ipynb)

## Descripción

Análisis de la relación entre **movilidad urbana** y **productividad económica** en las principales ciudades latinoamericanas durante 2024, basado en datos reales de TomTom Traffic Index y OECD Cities.

**Pregunta central:**
> ¿Qué relación existe entre la congestión vehicular y el PIB per cápita en ciudades latinoamericanas, y en qué ciudades conviene invertir en infraestructura de transporte?

---

## Datasets

| Archivo | Fuente | Descripción |
|---|---|---|
| `tomtom_traffic.csv` | TomTom Traffic Index | Indicadores de tráfico y congestión por ciudad |
| `oecd_city_economy.csv` | OECD Cities | Indicadores económicos: PIB per cápita, desempleo, contaminación, población |

### Variables clave

| Variable | Descripción |
|---|---|
| `jamsdelay` | Retraso total por congestión (minutos) |
| `trafficindexlive` | Índice de tráfico en tiempo real |
| `minsdelay` | Minutos de retraso por cada 10 km |
| `jamslengthinkms` | Longitud total de embotellamientos (km) |
| `city_gdp_capita` | PIB per cápita en USD |
| `unemployment_%` | Tasa de desempleo (%) |
| `pm2.5_ug_m3` | Contaminación del aire (μg/m³) |
| `population` | Población total de la ciudad |

---

## Estructura del análisis

| Paso | Contenido |
|---|---|
| 1 — Carga y exploración | Importación de librerías, carga de los 2 datasets y vista previa |
| 2 — Limpieza y preparación | Estandarización de nombres en snake_case, conversión de tipos, limpieza de separadores numéricos |
| 3 — Extracción de año y filtrado | Extracción de la columna `year` desde fechas, filtrado a 2024 |
| 4 — Resumen de movilidad | Promedios de tráfico por ciudad, país y año con `groupby` |
| 5 — Unión de datasets | Merge INNER entre tráfico y economía por `city` y `year` |
| 6 — Visualización | Boxplot de congestión, histograma de PIB, gráfico de barras comparativo |
| 7 — Exportación | Generación del CSV limpio `ladb_mobility_economy_2024_clean.csv` |

---

## Limpieza de datos realizada

| Problema | Columna | Acción tomada |
|---|---|---|
| Columnas en formato no estándar | Todos los datasets | Renombrado a `snake_case` con `.str.lower()` y `.str.replace()` |
| Fechas como `object` | `updatetimeutc`, `updatetimeutcweekago` | Conversión con `pd.to_datetime(errors='coerce')` |
| Números con separadores de miles (`.`) | `city_gdp_capita` | Limpieza de puntos y conversión a `float` |
| Porcentajes como texto (`%`) | `unemployment_%` | Eliminación del símbolo y conversión a `float` |
| Decimales con coma | `pm2.5_ug_m3`, `population_m` | Reemplazo de `,` por `.` y conversión a `float` |
| Población en millones | `population_m` | Creación de columna `population` multiplicada por 1,000,000 |

---

## Cobertura del análisis

- **Año analizado:** 2024
- **Ciudades incluidas:** 15
- **Países:** Brasil, Colombia, Argentina, Perú, México, Uruguay, Chile

---

## Principales hallazgos

- **Ciudad con mayor congestión:** Ciudad de México lidera en `jamsdelay` promedio.
- **Sin correlación lineal fuerte:** Las ciudades con alta congestión no necesariamente tienen bajo PIB per cápita; en algunos casos la congestión es consecuencia del crecimiento económico.
- **Outliers en congestión:** Al menos una ciudad supera 4 veces el promedio general, sesgando las estadísticas (mediana ~250 min vs. promedio ~630 min).
- **Ciudad prioritaria para inversión:** **Bogotá** presenta la mayor correlación entre altos niveles de congestión y bajo PIB per cápita, según el ratio congestión/productividad calculado frente a Lima y Buenos Aires.

---

## Recomendaciones

- **Bogotá** es la ciudad prioritaria para inversión en infraestructura de transporte, dado su alto ratio congestión/PIB per cápita.
- Segmentar el análisis en grupos de ciudades comparables antes de generalizar conclusiones.
- Validar la calidad de los datos TomTom para las ciudades con valores extremos (posibles eventos extraordinarios en 2024: obras viales, desastres naturales, eventos masivos).
- Complementar el análisis con datos longitudinales (más de un año) para identificar tendencias reales, no solo un corte temporal.

---

## Output generado

| Archivo | Descripción |
|---|---|
| `ladb_mobility_economy_2024_clean.csv` | Dataset limpio y combinado listo para análisis posterior |

---

## Tecnologías utilizadas

- Python 3
- pandas
- numpy
- matplotlib
- seaborn

---

## Cómo ejecutar el notebook

1. Haz clic en el badge **Abrir en Colab** al inicio del README.
2. Asegúrate de tener acceso a los datasets en la ruta `/datasets/`.
3. Ejecuta las celdas en orden secuencial (Paso 1 → Paso 7).
