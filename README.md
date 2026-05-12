# 📡 ConnectaTel — Análisis de Comportamiento de Clientes

Análisis exploratorio de datos de una empresa de telecomunicaciones latinoamericana, con el objetivo de entender el comportamiento de sus clientes, detectar patrones de uso y generar recomendaciones estratégicas basadas en segmentación.

---

## 🎯 Objetivo del proyecto

Evaluar el comportamiento de los clientes de **ConnectaTel** a partir de datos registrados hasta 2024, identificando:
- Patrones de consumo por plan y segmento
- Comportamientos atípicos (outliers y sentinels)
- Segmentos de clientes por edad y nivel de uso
- Oportunidades de retención y mejora de planes

---

## 📁 Datasets utilizados

| Archivo | Descripción | Filas |
|---|---|---|
| `plans.csv` | Información de los planes (precio, minutos, GB, costos por excedente) | 2 |
| `users_latam.csv` | Datos de clientes (edad, ciudad, fecha de registro, plan, churn) | 4,000 |
| `usage.csv` | Detalle de uso real: llamadas y mensajes por usuario | 40,000 |

---

## 🧩 Etapas del análisis

1. **Carga y exploración** — Revisión de estructura, tipos de datos y valores nulos en los tres datasets.
2. **Detección de inconsistencias** — Identificación de sentinels (`age = -999`, `city = "?"`), fechas futuras en `reg_date` y nulos estructurales en `usage`.
3. **Limpieza de datos** — Imputación de sentinels, reemplazo de valores inválidos y verificación MAR en columnas de uso.
4. **Agregación por usuario** — Construcción de métricas por usuario: total de llamadas, mensajes y minutos de llamada.
5. **Estadísticas descriptivas** — Resumen estadístico de variables numéricas y distribución de planes.
6. **Visualización y outliers** — Histogramas por plan y boxplots con método IQR para detectar valores extremos.
7. **Segmentación de clientes** — Clasificación por nivel de uso (Bajo / Medio / Alto) y por grupo de edad (Joven / Adulto / Adulto Mayor).
8. **Insight ejecutivo** — Conclusiones y recomendaciones accionables para el negocio.

---

## 🚀 Cómo ejecutar el notebook

### Opción A — Google Colab (recomendado)

1. Abre [Google Colab](https://colab.research.google.com/)
2. Ve a **File → Upload notebook** y sube el archivo `.ipynb`
3. Sube los tres archivos CSV desde el panel lateral (ícono de carpeta → subir archivo)
4. Actualiza las rutas de carga en la celda correspondiente:
   ```python
   plans = pd.read_csv('plans.csv')
   users = pd.read_csv('users_latam.csv')
   usage = pd.read_csv('usage.csv')
   ```
5. Ejecuta todas las celdas con **Runtime → Run all**

### Opción B — Jupyter local

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tu-usuario/tu-repositorio.git
   cd tu-repositorio
   ```
2. Instala las dependencias:
   ```bash
   pip install pandas matplotlib seaborn
   ```
3. Coloca los archivos CSV en la misma carpeta que el notebook
4. Abre el notebook:
   ```bash
   jupyter notebook
   ```

---

## 📦 Dependencias

```
pandas
matplotlib
seaborn
```

---

## 📊 Principales hallazgos

- El **64.9%** de los usuarios tiene el plan Básico y el **35.1%** el plan Premium.
- Se identificaron **3 segmentos de uso** usando percentiles: Bajo uso (45%), Uso medio (25%) y Alto uso (30%).
- La tasa de churn general es del **11.65%**, distribuida uniformemente entre segmentos.
- **781 usuarios de Alto uso permanecen en el plan Básico**, representando una oportunidad de upselling directa.
- Los **Adultos (50.5% de la base)** presentan la mayor tasa de churn (12.5%).

---

## 👤 Autor

Proyecto desarrollado como parte del Sprint 7 del bootcamp de análisis de datos.
