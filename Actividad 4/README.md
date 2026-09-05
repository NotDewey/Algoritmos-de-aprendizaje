# Actividad 3 - SVM y K-Means

En esta actividad se aplicaron técnicas de aprendizaje supervisado y no supervisado utilizando el dataset **Wisconsin Diagnostic Breast Cancer (WDBC)**.

## Objetivo

El objetivo fue analizar las características numéricas de muestras de tumores mamarios y comparar dos enfoques:

- **SVM**, para predecir si una muestra es benigna o maligna.
- **K-Means**, para identificar grupos naturales sin utilizar la variable de diagnóstico durante el entrenamiento.

## Dataset

**Nombre:** Wisconsin Diagnostic Breast Cancer (WDBC)  
**Fuente:** UCI Machine Learning Repository

El dataset contiene 569 registros y 30 variables numéricas relacionadas con características de los núcleos celulares.

La variable objetivo es:

- `B` = Benigno
- `M` = Maligno

La columna `id` se utilizó únicamente como identificador y no como variable predictora.

## Análisis supervisado - SVM

Se dividieron los datos en:

- 80% entrenamiento
- 20% prueba

Se utilizó `random_state=42` y estratificación para conservar la proporción de las clases.

Se entrenaron dos modelos SVM:

- SVM con kernel lineal
- SVM con kernel RBF

El escalamiento se realizó con `StandardScaler` dentro de un `Pipeline`.

Las métricas utilizadas fueron:

- Accuracy
- Precision
- Recall
- F1-score

El modelo con kernel RBF obtuvo el mejor desempeño general.

También se generó una matriz de confusión para analizar los errores del modelo y se compararon diferentes valores del hiperparámetro `C`.

## Análisis no supervisado - K-Means

Para K-Means se eliminaron temporalmente las columnas `id` y `diagnosis`.

Se probaron valores de `k` entre 2 y 6 utilizando:

- Método del codo
- Silhouette Score

El valor seleccionado fue:

**k = 2**

Este valor presentó la mejor separación entre grupos de acuerdo con el Silhouette Score y una estructura razonable según el método del codo.

Los clusters obtenidos fueron:

- Cluster 0: 375 registros
- Cluster 1: 194 registros

## PCA

Debido a que el dataset contiene 30 variables predictoras, se utilizó **PCA** para reducir los datos a dos componentes principales y poder visualizar los clusters.

Se generaron dos gráficas:

1. Observaciones coloreadas según el cluster asignado por K-Means.
2. Observaciones coloreadas según las clases reales.

Esto permitió comparar visualmente la estructura encontrada por K-Means con los diagnósticos originales.

## Comparación de clusters y clases reales

Después del entrenamiento de K-Means se compararon los clusters con las etiquetas reales.

Se encontró una correspondencia bastante clara entre ambos grupos y los diagnósticos benignos y malignos, aunque la coincidencia no fue perfecta.

Esto es esperado, ya que K-Means no utiliza las etiquetas reales para formar los grupos, sino que agrupa las observaciones de acuerdo con su similitud y distancia entre características.

## Conclusión

SVM resultó más fácil de interpretar para un problema de clasificación, ya que permite evaluar directamente qué tan bien se predicen clases conocidas.

K-Means permitió descubrir una estructura natural dentro de los datos sin utilizar previamente la variable objetivo.

En general:

- **SVM** es útil cuando existen etiquetas conocidas y se desea predecir la clase de nuevos registros.
- **K-Means** es útil cuando no existen etiquetas y se desea explorar grupos o patrones dentro de los datos.

## Archivos

- `Actividad3.ipynb` - Notebook con el análisis completo.
- `wdbc.data` - Dataset original.
- `wdbc_procesado.csv` - Dataset con los resultados del procesamiento y clusters asignados.

## Librerías utilizadas

- pandas
- numpy
- matplotlib
- scikit-learn
