Markdown
# 📞 ConnectaTel: Análisis de Comportamiento y Segmentación de Clientes (Hasta 2024)

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-orange.svg)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12+-green.svg)
![Contributions](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)

## 🎯 Objetivo del Proyecto

El objetivo principal de este proyecto es evaluar el comportamiento estratégico, comercial y operativo de los clientes de **ConnectaTel**, una empresa de telecomunicaciones en Latinoamérica, analizando el histórico de datos registrados hasta el año 2024. 

A través de este análisis de datos, se busca:
1. **Garantizar la calidad de la información:** Identificar y limpiar anomalías operativas (valores *sentinel*, fechas fuera de rango y datos ausentes).
2. **Construir perfiles estadísticos:** Comprender los patrones de consumo de los usuarios (mensajes, llamadas y minutos utilizados).
3. **Desarrollar segmentaciones de negocio:** Agrupar a los clientes bajo criterios de edad y nivel de uso para proponer estrategias de retención, optimización de infraestructura y diseño de ofertas comerciales.

---

## 📊 Datasets Utilizados

El análisis se alimenta de tres fuentes de datos interrelacionadas (archivos CSV):

| Archivo | Descripción | Variables Clave |
| :--- | :--- | :--- |
| **`plans.csv`** | Información técnica y comercial de las tarifas vigentes de la empresa. | `plan_name`, `usd_monthly_fee`, `minutes_included`, `messages_included`, `usd_per_message_extra` |
| **`users_latam.csv`** | Perfil demográfico y contractual de los clientes de la región. | `user_id`, `age`, `city`, `reg_date`, `plan`, `churn_date` |
| **`usage.csv`** | Bitácora transaccional y operativa del uso real de los servicios. | `id`, `user_id`, `date`, `type` (call/text), `duration` (minutos), `length` (caracteres) |

---

## 📑 Etapas del Análisis Realizadas

El proyecto se estructuró siguiendo el flujo de trabajo estándar de un proyecto de Ciencia de Datos:

1. **🧩 Carga y Exploración Inicial:** Conexión a las fuentes de datos, validación de estructuras con `.shape`, inspección de tipos de variables mediante `.info()` y vistas previas.
2. **🧼 Identificación y Limpieza de Calidad de Datos:**
   * Detección y corrección de valores *sentinel* (como edades con valor `-999` sustituidas por la mediana, y caracteres `'?'` en ciudades transformados a `pd.NA`).
   * Validación del comportamiento **MAR (Missing At Random)** en variables de consumo (`duration`/`length`).
   * Corrección de anomalías cronológicas (fechas de registro posteriores a 2024).
3. **📈 Agregación Estructurada (User Profile):** Consolidación de la bitácora transaccional en métricas acumuladas por usuario (`cant_mensajes`, `cant_llamadas`, `total_minutos_llamada`).
4. **📊 Visualización de Distribuciones y Outliers:** * Análisis del sesgo de los consumos mediante histogramas segmentados por el parámetro `hue='plan'`.
   * Implementación de bucles automáticos (`for`) para la generación de Boxplots y cálculo del Rango Intercuartílico ($IQR$). Evaluando mantener los *Heavy Users* por su valor comercial.
5. **🎯 Segmentación Estratégica:** Creación de etiquetas de negocio bajo lógica condicional (`grupo_uso` y `grupo_edad`).
6. **💡 Conclusiones Ejecutivas:** Elaboración de propuestas comerciales y de optimización de red dirigidas a los Stakeholders.

---

## 🚀 Cómo Ejecutar el Notebook

La libreta de este análisis fue diseñada para ser ejecutable tanto en entornos locales como en la nube.

### Ejecución Local (Jupyter Notebook / VS Code)
Si deseas clonar el repositorio de forma local, asegúrate de contar con Python 3.9 o superior instalado.

   
