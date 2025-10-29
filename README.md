# 🍺 Global Beer Analytics – Proyecto ETL y Visualización de Datos

<p align="center">
  <img src="./images/etl_medallion_architecture_diagram.svg" alt="Diagrama ETL con arquitectura Medallion" width="100%">
</p>

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![Polars](https://img.shields.io/badge/Polars-DataFrame-orange)
![Plotly](https://img.shields.io/badge/Plotly-Visualizaci%C3%B3n%20Interactiva-1f77b4?logo=plotly)
![ETL](https://img.shields.io/badge/Arquitectura-Bronce%E2%86%92Plata%E2%86%92Oro-success)
![License](https://img.shields.io/badge/licencia-MIT-green)

> **Proyecto abierto de ingeniería de datos** desarrollado con **Python, Polars y Plotly**,
> para analizar el consumo global de alcohol y su relación con el PIB y los niveles de ingreso (1960–2020).
> Construido paso a paso siguiendo la arquitectura **Medallion (Bronce → Plata → Oro)**.

---

## 🚀 Descripción general

**GlobalBeerAnalytics** es un proyecto ETL de punta a punta diseñado para:

* Practicar la construcción de **pipelines reales de ingeniería de datos**.
* Aplicar **limpieza, validación, enriquecimiento y visualización de datos**.
* Obtener **insights socioeconómicos** sobre el consumo global de bebidas alcohólicas.

Los datos provienen de **Our World in Data (OWID)** y de las **APIs abiertas del Banco Mundial**,
cubriendo más de 200 países a lo largo de 60 años de historia.

---

## 📊 Hallazgos y Visualizaciones Clave

Este conjunto de visualizaciones muestra la evolución del consumo de alcohol per cápita, su relación con el PIB, los niveles de ingreso y las regiones globales durante el periodo 1960–2020.

### 🧭 1. Relación PIB vs. Consumo (Animación Interactiva)

Esta es la visualización principal del proyecto, que anima la correlación entre la riqueza de un país (PIB per cápita) y su consumo de alcohol a lo largo de 60 años.

> 🎮 [**Ver visualización interactiva en GitHub Pages**](https://ericksootano.github.io/GlobalBeerAnalytics/data/gold/plots/pib_vs_consumo.html)
> 
> * **Hallazgo Clave (Relación PIB–Consumo):** Existe una clara **correlación positiva** entre el desarrollo económico y el consumo. A medida que el PIB per cápita de un país aumenta, también lo hace su consumo de alcohol, hasta que factores culturales, religiosos o de salud pública moderan esta relación.

---

### 📈 Visualizaciones Estáticas y sus Hallazgos

Las siguientes gráficas (archivos `.png` estáticos) descomponen las tendencias observadas en la animación principal.

#### 2. Consumo Promedio Global por Tipo de Bebida
![Consumo Global](./images/previews/consumo_global.png)

* **Hallazgo (Tendencia Global):** El consumo global de alcohol mostró un **incremento sostenido desde 1960 hasta cerca del año 2000**. A partir de las últimas dos décadas, esta tendencia tiende a estabilizarse a nivel mundial.

#### 3. Consumo por Grupo de Ingresos
![Consumo por Ingreso](./images/previews/consumo_por_ingreso.png)

* **Hallazgo (Grupos de Ingreso):** Los **países de altos ingresos** presentan, con diferencia, el mayor consumo per cápita. Paralelamente, los países de ingresos medios y bajos muestran un crecimiento más gradual pero constante, sugiriendo una convergencia a medida que se desarrollan.

#### 4. Consumo Promedio por Región
![Consumo por Región](./images/previews/consumo_por_region.png)

* **Hallazgo (Regiones):** **Europa y Norteamérica** dominan históricamente el consumo global de alcohol. Sin embargo, regiones como Asia y África, aunque con niveles base más bajos, muestran un aumento progresivo con una alta variabilidad entre países.

#### 5. Top 10 Países con Mayor Consumo (2020)
![Top 10 Países](./images/previews/top10_paises.png)

* **Hallazgo (Ranking):** Para el año 2020, el ranking de los 10 principales países consumidores está **dominado casi en su totalidad por naciones europeas**, reflejando patrones culturales de consumo profundamente arraigados.

---

### 🧠 Conclusiones Generales del Análisis

El análisis de 60 años de datos evidencia una relación clara entre el desarrollo económico y los patrones de consumo de alcohol:

* **El desarrollo impulsa el consumo:** Los países de altos ingresos lideran el consumo, mientras que los de ingresos bajos y medios crecen gradualmente, en paralelo con su PIB.
* **Estabilización reciente:** A nivel global, el consumo promedio parece haberse estabilizado desde el año 2000, aunque las tendencias regionales varían.
* **Liderazgo regional:** Europa y América del Norte siguen siendo las regiones con mayor consumo per cápita.
* **Influencia cultural:** Aunque el PIB es un fuerte predictor, la correlación no es perfecta, lo que demuestra que factores culturales, religiosos y políticos (como se ve en el Top 10) siguen siendo determinantes clave en el comportamiento del consumo.

---

## ⚙️ Instalación y configuración

### 1️⃣ Clonar el repositorio

```bash
git clone [https://github.com/ericksootano/GlobalBeerAnalytics.git](https://github.com/ericksootano/GlobalBeerAnalytics.git)
cd GlobalBeerAnalytics
```

### 2️⃣ Crear y activar entorno virtual

```bash
python -m venv .venv
source .venv/bin/activate  # En Windows: .venv\Scripts\activate
```

### 3️⃣ Instalar dependencias

```bash
pip install -r requirements.txt
```

### 4️⃣ Ejecutar el pipeline ETL

Ejecutar notebook:

```
notebooks/
 ├── GlobalBeerAnalytics_ETL.ipynb

```

---

## 🧱 Arquitectura del Proyecto – Modelo Medallion

```
Datos Crudos (OWID, Banco Mundial)
        ↓
🥑 Bronce → Archivos CSV crudos (cerveza, destilados, total)
        ↓
🥈 Plata  → Datos limpios, normalizados y enriquecidos (PIB, regiones, niveles de ingreso)
        ↓
🥇 Oro    → Tablas analíticas y visualizaciones interactivas
```

### 🧩 Tecnologías utilizadas

| Capa              | Herramientas / Librerías       | Descripción                                                            |
| ----------------- | ------------------------------ | ---------------------------------------------------------------------- |
| 🥉 Bronce         | `requests`, `pandas`, `json`   | Descarga y almacenamiento de datos desde OWID y APIs del Banco Mundial |
| 🥈 Plata          | `polars`, `pyarrow`            | Limpieza, normalización y control de calidad de los datos              |
| 🥇 Oro            | `plotly.express`, `matplotlib` | Análisis visual e interactividad                                       |
| 🧮 Utilidades     | `python-dotenv`, `glob`, `os`  | Automatización y manejo de archivos                                    |
| ☁️ Almacenamiento | Archivos Parquet locales       | Almacenamiento columnar optimizado para análisis                       |

---

## 🧮 Resumen del pipeline

### 🥑 Capa Bronce

* Descarga de datos crudos de consumo (cerveza, destilados, total).
* Se almacenan en `../data/bronze/*.csv` sin modificar.

### 🥈 Capa Plata

* Limpieza, normalización y auditoría de calidad con **Polars**.
* Creación del log de calidad `data_quality_log.parquet` con:
    * Total de registros, nulos eliminados, valores negativos corregidos y porcentaje de calidad.
* Enriquecimiento con **PIB per cápita** y **clasificación por región e ingreso del Banco Mundial**.

### 🥇 Capa Oro

* Generación de tablas analíticas en `/data/gold/`.
* Creación de visualizaciones interactivas con **Plotly**:
    * Tendencias globales por tipo de bebida.
    * Consumo promedio por región y grupo de ingreso.
    * Top 10 países con mayor consumo.
    * **Gráfico animado (PIB vs consumo de alcohol, 1960–2020)**.

---

## 🧮 Estructura del proyecto

```
GlobalBeerAnalytics/
│
├── data/
│   ├── bronze/                  # Datos crudos descargados
│   ├── silver/                  # Datos limpios y enriquecidos
│   └── gold/                    # Resultados analíticos y gráficos
│
├── images/
│   ├── previews/                # Imágenes de gráficos generados
│   │   ├── consumo_global.png
│   │   ├── consumo_por_ingreso.png
│   │   ├── consumo_por_region.png
│   │   ├── pib_vs_consumo.png
│   │   └── top10_paises.png
│   └── etl_medallion_architecture_diagram.svg # Diagrama de arquitectura
│
├── notebooks/
│   └── GlobalBeerAnalytics_ETL.ipynb
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## 🗂️ Diccionario de datos – Tabla final (Silver enriquecida / base Gold)

**Archivo:** `data/silver/alcohol_consumption_enriched.parquet`
**Uso:** insumo directo para todas las tablas y visualizaciones de la Capa Oro.

### Esquema y descripciones de columnas

| Columna              | Tipo      | ¿Nulos? | Descripción                                                                                                                      | Ejemplo                     |
| -------------------- | --------- | ------- | -------------------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| `country`            | `string`  | No      | Nombre del país según OWID/World Bank.                                                                                           | `Dominican Republic`        |
| `iso_code`           | `string`  | No      | Código **ISO 3166‑1 alpha‑3** (3 letras). **Clave recomendada** para joins con metadatos (regiones, PIB).                        | `DOM`                       |
| `year`               | `int32`   | No      | Año de referencia (rango típico **1960–2020**).                                                                                  | `2018`                      |
| `beverage_type`      | `string`  | No      | Tipo de bebida. Valores: `beer`, `spirits`, `total`.                                                                             | `beer`                      |
| `litres_per_capita`  | `float64` | No      | **Litros de alcohol puro per cápita por año**. Negativos corregidos a `0` en Capa Plata.                                         | `6.42`                      |
| `gdp_per_capita_usd` | `float64` | Sí      | **PIB per cápita (US$ corrientes)** del Banco Mundial. Puede faltar para algunos años/territorios.                               | `8543.72`                   |
| `region`             | `string`  | Sí      | Región del Banco Mundial (p. ej., `Latin America & Caribbean`). Algunos territorios pueden quedar como nulos.                    | `Latin America & Caribbean` |
| `income_group`       | `string`  | Sí      | Grupo de ingreso del Banco Mundial: `High income`, `Upper middle income`, `Lower middle income`, `Low income`, `Not classified`. | `Upper middle income`       |
| `lending_type`       | `string`  | Sí      | Tipo de financiación del Banco Mundial (e.g., `IBRD`, `IDA`, `Blend`, `Not classified`).                                         | `IBRD`                      |
| `capital_city`       | `string`  | Sí      | Capital administrativa informada por el Banco Mundial (referencial).                                                             | `Santo Domingo`             |

> 💡 **Unidades y definiciones**
>
> * `litres_per_capita` sigue la definición de OWID (**alcohol puro**). En Capa Plata se eliminan nulos y se corrigen negativos a `0`.
> * `gdp_per_capita_usd` es el indicador **NY.GDP.PCAP.CD** del Banco Mundial (US$ corrientes), sin ajuste por PPP.

### Clave y calidad de datos

* **Clave natural recomendada:** `iso_code`, `year`, `beverage_type` (garantiza unicidad por país‑año‑tipo).
* **Reglas de calidad aplicadas (Capa Plata):**
    * Eliminación de nulos en `litres_per_capita`.
    * Corrección de valores negativos en `litres_per_capita` → `0`.
    * Deduplicación por `country`, `iso_code`, `year`, `beverage_type`.
    * Bitácora en `data/silver/data_quality_log.parquet` con métricas por dataset.

### Sugerencia de DDL (si exportas a SQL)

```sql
CREATE TABLE dbo.AlcoholConsumptionEnriched (
    iso_code            CHAR(3)      NOT NULL,
    year                INT          NOT NULL,
    beverage_type       VARCHAR(16)  NOT NULL,
    country             VARCHAR(100) NOT NULL,
    litres_per_capita   FLOAT        NOT NULL,
    gdp_per_capita_usd  FLOAT        NULL,
    region              VARCHAR(64)  NULL,
    income_group        VARCHAR(32)  NULL,
    lending_type        VARCHAR(32)  NULL,
    capital_city        VARCHAR(64)  NULL,
    CONSTRAINT PK_AlcoholConsumptionEnriched PRIMARY KEY (iso_code, year, beverage_type)
);
```

> 📦 **Notas de particionado (Parquet):** para consultas rápidas en motores analíticos, puedes particionar por `year` o por `region`, según el patrón de acceso.

---

## 🧳 Limitaciones y próximos pasos

* Falta de información completa para algunos países y años.
* Posible integración futura con **Databricks** o **Power BI** para análisis a gran escala.
* Automatización del pipeline con **Airflow** o **Prefect**.
* Implementar pruebas unitarias y CI/CD para validación continua.

---

## 📦 Dependencias (`requirements.txt` actualizado)

```txt
certifi==2025.10.5
charset-normalizer==3.4.4
contourpy==1.3.3
cycler==0.12.1
fonttools==4.60.1
idna==3.11
kiwisolver==1.4.9
matplotlib==3.10.7
narwhals==2.9.0
numpy==2.3.4
packaging==25.0
pillow==12.0.0
plotly==6.3.1
polars==1.34.0
pyarrow==22.0.0
python-dateutil==2.9.0.post0
python-dotenv==1.1.1
requests==2.32.5
six==1.17.0
urllib3==2.5.0
pandas==2.2.3
```

---

## 🧑‍💻 Autor

**Erickson Otaño Sánchez**
*Ingeniero de Datos | Desarrollador ETL | Analista de Información*
📍 Cervecería Nacional Dominicana (AB InBev)
🔗 [LinkedIn](https://www.linkedin.com/in/erickson-otaño/)

---

## 🩶 Licencia

Este proyecto se distribuye bajo la **licencia MIT**.
Eres libre de usarlo, modificarlo y compartirlo con fines educativos o de portofolio.

---

## 👌 Agradecimientos

* **Our World in Data** por el dataset de consumo de alcohol.
* **Banco Mundial (World Bank API)** por los datos económicos y de clasificación.
* **Comunidades de Polars y Plotly** por sus herramientas excepcionales.
* Proyecto desarrollado con ❤️ como parte del *viaje de aprendizaje de ingeniería de datos en Python*.