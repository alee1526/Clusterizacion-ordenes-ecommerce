# Clusterización de Órdenes de Supermercados en Plataformas Digitales

Este proyecto realiza una clusterización de 500,000 órdenes de supermercados provenientes de una plataforma digital de pedidos (PedidosYa), utilizando los algoritmos **K-Means** y **Gaussian Mixture Models (GMM)** para identificar patrones de compra. Ambos métodos se implementan con **k=5 clusters**, explorando y comparando sus resultados para detectar distintos tipos de comportamientos de consumo. El trabajo forma parte del curso **Taller de Analítica de Datos** del **Master en Big Data** de la **Universidad ORT Uruguay**.

## Descripción

El objetivo es segmentar las órdenes de supermercados según características transaccionales, temporales y de producto, con el fin de comprender los hábitos y motivaciones de los usuarios. Se emplean dos enfoques de clusterización:

- **K-Means**: Método basado en centroides para agrupar órdenes en 5 clusters.
- **Gaussian Mixture Models (GMM)**: Modelo probabilístico que asigna órdenes a 5 clusters basados en distribuciones gaussianas.

El análisis incluye un **Análisis Exploratorio de Datos (EDA)** inicial y la generación de una tabla analítica para la clusterización, seguida de la aplicación y evaluación de ambos modelos.

## Estructura del Proyecto

- **`EDA.ipynb`**: Notebook que realiza el análisis exploratorio de datos (EDA), generando visualizaciones, estadísticas descriptivas y la tabla para clusterización.
- **`Gaussian.ipynb`**: Notebook que implementa la clusterización con GMM (k=5), incluyendo preprocesamiento, reducción de dimensionalidad (PCA), modelado y visualización.
- **`Kmeans.ipynb`**: Notebook que implementa la clusterización con K-Means (k=5), incluyendo preprocesamiento, método del codo, modelado y visualización.

**Nota**: Los archivos de datos (e.g., órdenes, productos, embeddings) no están incluidos en el repositorio debido a su naturaleza confidencial o tamaño. Los notebooks asumen que los datos están disponibles localmente en el formato descrito en el informe.

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
   git clone https://github.com/alee1526/Clusterizacion-ordenes-ecommerce.git
   cd Clusterizacion-ordenes-ecommerce
   ```

2. **Obtener los datos**:

   - Los notebooks requieren archivos de datos (e.g., `ordenes_caso_peya.csv`, `productos_embeddings_peya.csv`, `productos_orders_peya.csv`, `tabla_para_clusterizacion.csv`). Estos no están incluidos en el repositorio.
   - Asegúrate de tener los datos en el directorio correcto o ajusta las rutas en los notebooks según corresponda.

3. **Instalar dependencias**:

   - Ejecuta el comando de instalación de bibliotecas mencionado arriba o verifica que estén instaladas.

4. **Ejecutar el EDA**:

   - Abre `EDA.ipynb` en Jupyter Notebook.
   - Asegúrate de que los datos requeridos estén disponibles.
   - Ejecuta las celdas para explorar los datos y generar la tabla para clusterización.
   - Si tienes archivos intermedios precomputados, ajusta la variable `Flag = False` en el notebook para cargarlos y ahorrar tiempo.

5. **Ejecutar las clusterizaciones**:

   - **K-Means**: Abre `Kmeans.ipynb` y ejecuta las celdas. Requiere la tabla generada en el EDA.
   - **GMM**: Abre `Gaussian.ipynb` y ejecuta las celdas. También usa la tabla del EDA.
   - Los resultados se guardan en archivos CSV (e.g., `kmeans_resultados.csv`, `GMM_resultados.csv`). Usa `Flag = False` para cargar resultados precomputados si están disponibles.

6. **Explorar resultados**:

   - Revisa las visualizaciones (e.g., TSNE, gráficos de barras) en los notebooks para interpretar los clusters.

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

Desarrollado como parte del curso **Taller de Analítica de Datos**, **Master en Big Data**, **Universidad ORT Uruguay**.
