# Actividad 1 - Preparación de datos

En este repositorio está mi actividad sobre limpieza y preparación de datos usando el dataset **Student Performance Factors**.

El objetivo fue revisar el estado inicial del dataset, detectar problemas de calidad y dejar una versión más preparada para poder utilizarla después en un modelo de aprendizaje automático.

## Archivos

* `Actividad_1.ipynb`: contiene todo el proceso de análisis, limpieza y transformación.
* `StudentPerformanceFactors_preparado.csv`: versión final del dataset después de realizar la limpieza y algunas transformaciones.

## Dataset

Se utilizó el dataset **Student Performance Factors** de Kaggle, el cual contiene diferentes factores que pueden influir en el desempeño académico de los estudiantes.

La variable que se tomó como posible objetivo fue `Exam_Score`, ya que representa el puntaje obtenido por cada estudiante y posteriormente podría utilizarse en un problema de regresión.

## Lo que se realizó

Durante la actividad se revisaron valores faltantes, duplicados, tipos de datos, categorías, valores extremos y rangos incorrectos.

También se realizaron algunas transformaciones como:

* Imputación de valores faltantes.
* Eliminación de un valor imposible en `Exam_Score`.
* One-Hot Encoding para `School_Type`.
* Codificación ordinal para `Motivation_Level`.
* Escalamiento de variables numéricas con `StandardScaler`.
* Organización de las transformaciones mediante `ColumnTransformer`.

Al final, el dataset quedó con **6,606 registros y 20 variables**, sin valores faltantes ni registros duplicados y conservando `Exam_Score` como posible variable objetivo para una etapa posterior de modelado.
