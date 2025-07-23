# Clusterizacion-de-ordenes-de-Supermercados-en-Plataformas-Digitales

Este proyecto realiza una clusterización de 500,000 órdenes de supermercados provenientes de una plataforma digital de pedidos (PedidosYa), utilizando los algoritmos K-Means y Gaussian Mixture Models (GMM) para identificar patrones de compra. Ambos métodos se implementan con k=5 clusters, explorando y comparando sus resultados para detectar distintos tipos de comportamientos de consumo. El trabajo forma parte del curso "Taller de Analítica de Datos" del Master en Big Data de la Universidad ORT Uruguay.

## Descripción

El objetivo es segmentar las órdenes de supermercados según características transaccionales, temporales y de producto, con el fin de comprender los hábitos y motivaciones de los usuarios. Se emplean dos enfoques de clusterización:

- **K-Means**: Método basado en centroides para agrupar órdenes en 5 clusters.
- **Gaussian Mixture Models (GMM)**: Modelo probabilístico que asigna órdenes a 5 clusters basados en distribuciones gaussianas.

El análisis incluye un Análisis Exploratorio de Datos (EDA) inicial y la generación de una tabla analítica para la clusterización, seguida de la aplicación y evaluación de ambos modelos.

## Estructura del Proyecto

- `EDA.ipynb`: Notebook que realiza el análisis exploratorio de datos (EDA) sobre las tablas madre, generando visualizaciones, estadísticas descriptivas y la tabla para clusterización (`tabla_para_clusterizacion.csv`).
- `Gaussian.ipynb`: Notebook que implementa la clusterización con GMM (k=5), incluyendo preprocesamiento, reducción de dimensionalidad (PCA), modelado y visualización.
- `Kmeans.ipynb`: Notebook que implementa la clusterización con K-Means (k=5), incluyendo preprocesamiento, método del codo, modelado y visualización.
- `ordenes_caso_peya.csv`: Tabla madre con información detallada de las órdenes (order_id, día, hora, vendor_id, user_id, monto total, descuentos).
- `productos_embeddings_peya.csv`: Tabla madre con información de productos, incluyendo embeddings (product_name_hash, level_one_hash, level_two_hash, emb_str).
- `productos_orders_peya.csv`: Tabla madre que relaciona órdenes con productos (order_id, product_name_hash).
- `tabla_para_clusterizacion.csv`: Tabla generada por `EDA.ipynb`, con variables derivadas para la clusterización (e.g., total_amount, cant_prod_por_ped, log_sum_pairwise_cooc).
- `GMM_resultados.csv`: Resultados de las etiquetas de clusterización GMM.
- `kmeans_resultados.csv`: Resultados de las etiquetas de clusterización K-Means.
- **Archivos intermedios**:
  - `EDA_embeddings_df.csv`, `EDA_prod_por_orden.csv`, `EDA_prod_por_orden_con_duplicados.csv`: Generados en EDA para agilizar ejecución.
  - `GMM_tsne_results.csv`, `kmeans_pca_results.csv`, `kmeans_tsne_results.csv`, `kmeans_wcss_df.csv`, `kmeans_elem_min.csv`: Resultados intermedios de visualización y evaluación.
- `Obligatorio TAD - Entrega 2 - DiazDiazZalovich.pdf`: Informe completo con detalles del análisis y resultados.

## Requisitos

Para ejecutar los notebooks, necesitas las siguientes dependencias:

- **Python 3.x**
- **Bibliotecas**:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `scikit-learn`
  - `jupyter`

Puedes instalarlas con:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

## Instrucciones de Uso

1. **Clonar el repositorio**:

   ```bash
   git clone https://github.com/alee1526/Clusterizacion-de-ordenes-de-Supermercados-en-Plataformas-Digitales.git
   cd Clusterizacion-de-ordenes-de-Supermercados-en-Plataformas-Digitales
   ```

2. **Instalar dependencias**: Ejecuta el comando anterior o asegúrate de tener las bibliotecas listadas.

3. **Ejecutar el EDA**:

   - Abre `EDA.ipynb` en Jupyter Notebook.
   - Ejecuta las celdas para explorar los datos y generar `tabla_para_clusterizacion.csv`.
   - Si prefieres evitar cálculos costosos, usa los archivos CSV intermedios (`EDA_*.csv`) ajustando la variable `Flag = False`.

4. **Ejecutar las clusterizaciones**:

   - **K-Means**: Abre `Kmeans.ipynb` y ejecuta las celdas. Requiere `tabla_para_clusterizacion.csv`.
   - **GMM**: Abre `Gaussian.ipynb` y ejecuta las celdas. También usa `tabla_para_clusterizacion.csv`.
   - Los resultados se guardan en `kmeans_resultados.csv` y `GMM_resultados.csv`. Usa `Flag = False` para cargar resultados precomputados y ahorrar tiempo.

5. **Explorar resultados**:

   - Revisa las visualizaciones (e.g., TSNE, gráficos de barras) en los notebooks.

## Resultados

### K-Means (k=5)

- **Cluster 0 – Compras planificadas y rutinarias (39.1%)**: Órdenes medianas, equilibradas, frecuentes en tardes/noches entre semana, con descuentos.
- **Cluster 1 – Compras específicas e impulsivas (12.1%)**: Pedidos pequeños (1 producto premium), sin descuentos, nocturnos o de fin de semana.
- **Cluster 2 – Compras de alto volumen (16.2%)**: Carritos grandes, alta diversidad, concentrados en fines de semana.
- **Cluster 3 – Compras mixtas y oportunistas (15.2%)**: Volumen moderado, descuentos frecuentes, flexibles en horario.
- **Cluster 4 – Compras exploratorias y especializadas (17.5%)**: Pedidos pequeños, categorías específicas, alternan semana/fin de semana.

### Gaussian Mixture Models (k=5)

- **Cluster 0 – Equilibradas y planificadas (18.6%)**: Variedad moderada, tardes/noches laborales.
- **Cluster 1 – Funcionales y acotadas (21.8%)**: Pedidos simples, alta rotación, horarios diurnos.
- **Cluster 2 – Urgentes y monocategoría (10.7%)**: Un producto caro, sin descuentos, noches.
- **Cluster 3 – Amplias y promocionales (34.7%)**: Alto volumen, descuentos, horarios pico.
- **Cluster 4 – Selectivas y especializadas (14.2%)**: Productos distintivos, fines de semana.

## Créditos

Desarrollado como parte del curso "Taller de Analítica de Datos", Master en Big Data, Universidad ORT Uruguay.
