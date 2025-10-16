# 📊 Análisis Global de Ventas de Notebooks por Marca (2020-2024)

Este proyecto analiza el comportamiento global de las ventas de notebooks entre 2020 y 2024, evaluando métricas como **ingresos totales**, **unidades vendidas**, **participación de mercado** y **tendencias por marca**.  

La solución implementa un flujo de datos **end-to-end** utilizando **AWS S3** para almacenamiento, **Amazon Athena** para consultas SQL sin servidores y **Tableau** para visualización interactiva.

---

## 🎯 Objetivos del Análisis

- Identificar las **marcas líderes en ingresos y ventas** a nivel global.  
- Analizar la **evolución anual de las ventas** y su comportamiento por región.  
- Determinar la **participación de mercado** de cada marca.  
- Detectar **patrones y tendencias** relevantes para la toma de decisiones estratégicas.  

---

## 🚀 Pipeline del Proyecto

<img src="Imagenes/Pipeline.png" alt="Descripción de la imagen" width="600">


1. **Dataset CSV (local)** → Archivo histórico de ventas de notebooks.
2. **AWS S3** → Carga del dataset a un bucket para almacenamiento seguro.
3. **Amazon Athena** → Creación de tabla externa y consultas SQL sobre los datos en S3.
4. **Tableau** → Conexión directa con Athena para construir el dashboard final.

---
## 📂 Estructura del Proyecto

<img src="Imagenes/estructura.png" alt="Descripción de la imagen" width="600">

---
## 📜 Consultas SQL en Athena

Todas las consultas están en la carpeta **`Queries/`**.  
Ejemplo: *Top 5 marcas por ingresos totales*  

<img src="Imagenes/consulta.png" alt="Descripción de la imagen" width="600">
---
## 📜 Control de calidad de datos

| Validación                | Regla Aplicada                                    | Resultado                  |
| ------------------------- | ------------------------------------------------- | -------------------------- |
| **Duplicados**            | `DISTINCT id_venta`                               | ✅ 0 duplicados             |
| **Nulos críticos**        | En `brand`, `year`, `revenue_usd` → eliminados    | ✅ Completitud > 99.5 %     |
| **Outliers**              | `revenue_usd < 1000 OR > 300000` → filtrados      | ✅ 1.1 % de filas filtradas |
| **Consistencia temporal** | `year BETWEEN 2020 AND 2024`                      | ✅ 100 % consistente        |
| **Tipos de datos**        | `CAST(year AS INT)`, `CAST(revenue_usd AS FLOAT)` | ✅ Tipado correcto          |


---
## 🔁 Incrementalidad & Idempotencia
En producción, el pipeline está preparado para ejecutar cargas incrementales e idempotentes.

<img src="Imagenes/consulta2.png" alt="Descripción de la imagen" width="600">
✅ Esto garantiza que el resultado final sea consistente aunque el proceso se ejecute varias veces.

## 📊 Visualizaciones del Dashboard

<img src="Imagenes/dashboard.png" alt="Descripción de la imagen" width="800">

El dashboard incluye:

1. **Ingreso vs Unidades vendidas por marca** – Gráfico de dispersión que relaciona ventas e ingresos con el precio promedio.
2. **Top 5 marcas por ingresos totales** – Barras horizontales que muestran las marcas más rentables.
3. **Tendencia de unidades vendidas (Top 5)** – Gráfico de líneas para ver la evolución anual.
4. **Unidades vendidas por continente y marca** – Barras apiladas para comparar regiones.
5. **Participación de mercado global** – Ranking global de unidades vendidas.
6. **Mapa de calor de ventas por año y marca** – Comparación visual de rendimiento histórico.


## 📈 Conclusiones Detalladas

1. **Liderazgo por ingresos**  
   - **Huawei** lidera con más de **$113B** acumulados.  
   - **MSI** y **Asus** siguen de cerca con cifras superiores a los **$90B**.

2. **Picos y caídas**  
   - **HP** tuvo un pico en 2021, triplicando sus ventas respecto a 2020, para luego caer de forma sostenida.

3. **Estabilidad vs. volatilidad**  
   - **Apple** y **Microsoft** muestran estabilidad.  
   - **Lenovo** y **Samsung** presentan variaciones abruptas, destacando el crecimiento de Samsung en 2023.

4. **Tendencias por región**  
   - **Asia y Europa** son los mercados más fuertes, con predominio de Huawei, Asus y MSI.  
   - **América** tiene una distribución más equilibrada de marcas.

5. **Relación precio–volumen**  
   - **Dell** y **Apple** tienen precios promedio más altos, con menor volumen (segmento premium).  
   - **HP** y **Lenovo** priorizan precios competitivos para aumentar ventas.

6. **Participación de mercado**  
   - Huawei domina globalmente, mientras MSI y Asus se consolidan como fuertes competidores.

7. **Oportunidades**  
   - **África y Oceanía** ofrecen potencial de crecimiento.  
   - Samsung podría capitalizar su crecimiento de 2023 para expandirse.

---

## 👤 Autor
Octavio Alvarez - Data Engineer

