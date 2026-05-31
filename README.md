# telecom-analysis

# 📡 ConnectaTel — Análisis de Comportamiento de Clientes

> Proyecto final del Sprint 7 | TripleTen Data Analytics Bootcamp 2026  
> Análisis exploratorio, limpieza de datos, segmentación y generación de insights para una empresa de telecomunicaciones en Latinoamérica.

---

## 📋 Descripción del Proyecto

ConnectaTel es una empresa de telecomunicaciones con presencia en Latinoamérica. Este proyecto analiza el comportamiento de sus clientes utilizando datos registrados hasta el año 2024, con el objetivo de:

- Detectar y corregir problemas de calidad en los datos
- Construir un perfil estadístico de los usuarios
- Identificar patrones de consumo y comportamientos atípicos
- Segmentar clientes por nivel de uso y rango de edad
- Generar recomendaciones estratégicas para mejorar la oferta de planes

---

## 🗂️ Datasets Utilizados

| Archivo | Descripción |
|---|---|
| `plans.csv` | Información de los planes disponibles: precio, minutos incluidos, GB incluidos y costo por excedente |
| `users_latam.csv` | Datos de los clientes: edad, ciudad, fecha de registro, plan contratado y fecha de baja (churn) |
| `usage.csv` | Detalle del uso real de servicios: llamadas y mensajes por usuario |

---

## 🔬 Etapas del Análisis

### 1. Carga y exploración inicial
- Importación de los tres datasets
- Revisión de estructura, tipos de datos y primeras filas

### 2. Identificación de problemas de calidad
- Detección de valores nulos por columna y proporción
- Identificación de valores sentinels (`-999` en `age`, `"?"` en `city`)
- Revisión y estandarización de columnas de fecha

### 3. Limpieza de datos
- Reemplazo del sentinel `-999` por la mediana de `age`
- Reemplazo de `"?"` por `NaN` en la columna `city`
- Marcado como `NaT` de fechas fuera de rango (año 2026 en `reg_date`)
- Validación de nulos estructurales (MAR) en `duration` y `length`

### 4. Agregación de métricas de uso por usuario
- Cálculo de: total de mensajes, total de llamadas y total de minutos por usuario
- Construcción del perfil consolidado `user_profile` (users + usage)

### 5. Visualización de distribuciones
- Histogramas por plan (Básico / Premium) para: edad, mensajes, llamadas y minutos
- Análisis de forma de distribución (simetría, sesgo)

### 6. Detección de outliers
- Boxplots por variable y plan
- Cálculo de límites con el método IQR
- Decisión justificada sobre mantener outliers (usuarios de alto valor)

### 7. Segmentación de clientes
- **Por nivel de uso:** Bajo uso / Uso medio / Alto uso
- **Por edad:** Joven / Adulto / Adulto Mayor
- Visualización de la distribución de segmentos

### 8. Análisis ejecutivo para stakeholders
- Resumen de problemas de datos detectados
- Insights por segmento de edad y nivel de uso
- Patrones de uso extremo y sus implicaciones de negocio
- Recomendaciones estratégicas para ConnectaTel

---

## 💡 Principales Hallazgos

- El **88.35%** de los registros en `churn_date` son nulos — la mayoría de clientes siguen activos.
- Se encontraron **sentinels** en `age` (`-999`) y `city` (`"?"`) que requerían corrección antes del análisis.
- Los **outliers en mensajes, llamadas y minutos** representan usuarios de alto valor, no errores de datos.
- El segmento de **Bajo uso es el más numeroso**, lo que indica riesgo de churn y oportunidad de reactivación.
- Los usuarios del plan **Premium** concentran mayor consumo de minutos y tienden a tener entre 35 y 50 años.
- Existe una **brecha entre los planes Básico y Premium** que justifica crear un plan intermedio.

---

## ▶️ Cómo ejecutar el notebook

### Opción 1 — Google Colab (recomendado)

1. Abre [Google Colab](https://colab.research.google.com/)
2. Ve a `File → Open notebook → GitHub`
3. Pega la URL de este repositorio y selecciona el archivo `.ipynb`
4. Asegúrate de subir los datasets a la ruta `/datasets/` o ajusta los paths en las celdas de carga

### Opción 2 — Jupyter Notebook local

```bash
# Clona el repositorio
git clone https://github.com/tu-usuario/tu-repositorio.git
cd tu-repositorio

# Instala las dependencias
pip install pandas numpy matplotlib seaborn

# Abre el notebook
jupyter notebook telecom-analysis_-_proyecto_sprint_7.ipynb
```

> ⚠️ Asegúrate de que los archivos CSV estén disponibles en la ruta `/datasets/` o actualiza los `pd.read_csv()` con la ruta correcta en tu entorno local.

---

## 🛠️ Tecnologías y Librerías

- **Python 3.x**
- `pandas` — manipulación y limpieza de datos
- `numpy` — operaciones numéricas
- `matplotlib` — visualizaciones base
- `seaborn` — visualizaciones estadísticas

---

## 👤 Autor

**Jhon** — Junior Data Analyst  
Bootcamp TripleTen Data Analytics · 2026  
📍 Bogotá, Colombia

---

## 📄 Licencia

Este proyecto fue desarrollado con fines educativos como parte del programa de formación de TripleTen.
