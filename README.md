# Segmentación Socioeconómica de Países usando K-Means Clustering

**Creado por:** María Isabel Zuluaga Quintero, Santiago Machado Serna
**Implementada la GUI por:** Kevin Sebastián Cifuentes, Sebastian Valencia Valencia

## Descripción

Este proyecto implementa el algoritmo **K-Means Clustering** en Python utilizando **pandas** y **numpy**. Se trata de un enfoque de aprendizaje automático no supervisado que permite agrupar datos en clusters según sus similitudes. Su aplicación incluye segmentación de clientes, reconocimiento de patrones y análisis socioeconómico.

## Arquitectura del Proyecto

```
machine_learning/
├── src/
│   ├── __init__.py
│   ├── model/
│   │   ├── kmeans_logic.py
│   │   ├── __init__.py
│   │   ├── errors/
│   │   │   ├── kmeans_error.py
│   │   │   ├── __init__.py
│   ├── view/
│   │   ├── console/
│   │   │   ├── kmeans_console_view.py
│
└── tests/
    ├── kmeans_test.py
    ├── __init__.py

│   casos_prueba.xlsx
│   datos_prueba.csv
│   estructura.txt
│   poetry.lock
│   pyproject.toml
│   README.md
```

## Instalación y Configuración

### **1. Requisitos Previos**

- Python 3.6 o superior
- Poetry para la gestión de dependencias

### **2. Clonar el Repositorio**

```sh
git clone https://github.com/sanma613/machine_learning.git
cd machine_learning
```

### **3. Instalar Dependencias**

```sh
poetry install
```

---

## Uso del Proyecto

### **Ejecutar la Interfaz de Consola**

```sh
python src/view/console/kmeans_console_view.py
```

- Se solicitará el dataset a clusterizar (por defecto hay un dataset de prueba en la raíz del proyecto).
- El dataset debe contener las siguientes columnas: `GDP_per_capita`, `life_expectancy`, `literacy_rate`.
- Se indicará el número de centroides deseados y las iteraciones máximas.
- Un mayor número de iteraciones mejora la precisión de los resultados.

### **Ejecutar Pruebas Unitarias**

```sh
python -m unittest tests/kmeans_test.py
```

Se incluyen:

- **3 casos de prueba normales**
- **3 casos de prueba extraordinarios**
- **4 casos de error**

---

## **Ejecutar la interfaz gráfica de usuario**

```sh
python src/view/gui/kmeans_gui.py
```

- **Descripción:** La interfaz gráfica permite cargar un dataset, configurar los parámetros del algoritmo K-Means (número de centroides y número máximo de iteraciones) y visualizar los resultados en gráficos interactivos.

- **Entradas:**

  * Ruta del dataset: Archivo CSV con las columnas GDP_per_capita, life_expectancy y literacy_rate.
  * Número de centroides: Entero positivo que define el número de clusters.
  * Iteraciones máximas: Entero positivo que indica el número máximo de iteraciones.

- **Salidas:**

  * Gráfico 3D de los clusters generados.
  * Gráficos 2D comparativos de las características del dataset.

- **Pasos:**

  * Ejecuta el comando anterior para iniciar la interfaz gráfica.
  * Ingresa la ruta del dataset en el campo correspondiente.
  * Especifica el número de centroides y las iteraciones máximas.
  * Haz clic en el botón "Mostrar Gráficos" para ejecutar el algoritmo y visualizar los resultados.
  * Si deseas reiniciar el formulario, haz clic en el botón "Reiniciar".
  
**Nota:** Asegúrate de que el archivo CSV esté correctamente formateado y contenga las columnas requeridas. Puedes usar el archivo datos_prueba.csv incluido en el repositorio como ejemplo.

## 📥 Entradas del Algoritmo

- **Dataset**: DataFrame de pandas con datos numéricos. Cada fila representa un punto de datos y cada columna una característica.
- **num_centroids**: Entero positivo que define el número de clusters.
- **max_i**: Entero positivo que indica el número máximo de iteraciones.

## 📤 Salidas del Algoritmo

- **Coordenadas de los centroides refinados**: Lista de tuplas con los centroides finales.
- **Dataset modificado** que incluye:
  - Datos normalizados para `GDP_per_capita`, `life_expectancy` y `literacy_rate`.
  - Columna `assigned_cluster`: Índice del cluster asignado a cada punto de datos.

---

## Proceso de K-Means

1. **Inicialización:** Se seleccionan aleatoriamente `k` centroides a partir de los datos.
2. **Asignación de clusters:** Cada punto se asigna al centroide más cercano.
3. **Actualización de centroides:** Se recalculan los centroides como la media de los puntos asignados a cada cluster.
4. **Iteración:** Se repiten los pasos hasta que los centroides se estabilizan o se alcanza el número máximo de iteraciones.

---

## 📊 Casos de Prueba

Un archivo en Excel (`casos_prueba.xlsx`) contiene al menos **10 casos de prueba** usados para validar el algoritmo:

- **3 casos normales**
- **3 casos extraordinarios**
- **4 casos de error**

Los resultados pueden ser verificados con las pruebas unitarias incluidas en el repositorio.

---

## 📌 Recomendaciones

- Se recomienda usar el dataset de prueba incluido en el repositorio.
- Si creas tu propio dataset, asegúrate de incluir `GDP_per_capita`, `life_expectancy` y `literacy_rate`.
- Antes de ejecutar el algoritmo, revisa que los datos sean numéricos y no contengan valores nulos.
- Experimenta con diferentes valores de `num_centroids` y `max_i` para obtener mejores resultados.
- Utiliza herramientas de visualización para analizar la segmentación realizada por el modelo.
