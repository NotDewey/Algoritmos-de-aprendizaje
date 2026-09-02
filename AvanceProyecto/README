Avance de Proyecto — Riesgo comercial de películas

Proyecto de Algoritmos de Aprendizaje Automático enfocado en identificar si una película tiene riesgo de no superar su presupuesto de producción en taquilla.

Objetivo

La idea del proyecto es usar información disponible antes o alrededor del estreno de una película para clasificarla en una de dos categorías:

CommercialRisk = 0: la película superó su presupuesto en taquilla.

CommercialRisk = 1: la película no superó su presupuesto en taquilla.

Como interesa detectar los proyectos que sí presentan riesgo, una de las métricas más importantes durante el análisis es el recall, ya que un falso negativo significaría clasificar una película como de bajo riesgo cuando realmente sí tenía riesgo comercial.

Dataset

Se utiliza el TMDB 5000 Movie Dataset, disponible en Kaggle:

https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata

Archivos utilizados:

tmdb_5000_movies.csv

tmdb_5000_credits.csv

Los dos archivos se combinan para obtener información de presupuesto, duración, género, idioma, fecha de estreno, director, reparto y productora, entre otras variables.

Proceso realizado

Durante el avance se trabajó en:

Carga y unión de los datasets.

Exploración inicial de los datos.

Revisión de valores faltantes, duplicados, tipos de datos y valores atípicos.

Creación de la variable objetivo CommercialRisk.

Revisión de posibles fugas de información.

Análisis exploratorio.

Separación de variables predictoras y variable objetivo.

División de los datos en entrenamiento, validación y prueba.

Construcción de un pipeline de preprocesamiento.

Entrenamiento y comparación de modelos iniciales.

Evaluación mediante distintas métricas.

Análisis de falsos negativos y del umbral de decisión.

Propuesta de mejoras para la siguiente etapa.

Partición de los datos

Se utiliza una división:

70% entrenamiento

15% validación

15% prueba

La partición usa random_state = 42 y estratificación para mantener una proporción similar de clases en los tres conjuntos.

El conjunto de prueba se mantiene separado para utilizarlo únicamente en la evaluación final.

Preprocesamiento

El preprocesamiento se realiza mediante Pipeline y ColumnTransformer.

Variables numéricas

Imputación con mediana.

Estandarización con StandardScaler.

Transformación log1p para budget.

Variables categóricas

Imputación con Unknown.

Codificación mediante OneHotEncoder.

handle_unknown="ignore".

Agrupación de categorías poco frecuentes con min_frequency=5.

El pipeline se ajusta solamente con los datos de entrenamiento para evitar fuga de información.

Modelos iniciales

Se compararon tres modelos:

DummyClassifier como baseline.

Regresión Logística.

Árbol de Decisión.

La Regresión Logística presentó el mejor resultado inicial de los modelos evaluados.

Modelo

Accuracy

Precision

Recall

F1-score

ROC-AUC

DummyClassifier

0.7562

0.0000

0.0000

0.0000

0.5000

Regresión Logística

0.7583

0.5714

0.0339

0.0640

0.5770

Árbol de Decisión

0.7541

0.3333

0.0085

0.0165

0.5576

Aunque la Regresión Logística fue la mejor opción inicial, su recall todavía es demasiado bajo para considerar que el problema está resuelto.

Ajuste del umbral

También se probó bajar el umbral de decisión de la Regresión Logística de 0.50 a 0.30.

Con este cambio:

El recall aumentó de 3.39% a 24.58%.

El F1-score aumentó de 6.40% a 28.71%.

La precision disminuyó debido al aumento de falsos positivos.

Esto muestra que el umbral será una parte importante de la siguiente fase del proyecto.

Limitaciones actuales

Las principales limitaciones encontradas son:

El recall todavía es bajo.

Los modelos generan demasiados falsos negativos.

El mejor ROC-AUC inicial sigue estando cerca de 0.5.

Algunas variables tienen alta cardinalidad.

Existen registros con budget o revenue igual a cero que no pueden utilizarse de forma confiable para construir la variable objetivo.

Próximos pasos

Para la entrega final se planea:

Probar Random Forest y Gradient Boosting.

Ajustar hiperparámetros.

Probar class_weight.

Usar validación cruzada estratificada.

Revisar selección de características.

Comparar diferentes umbrales.

Analizar interpretabilidad y desempeño por subgrupos.

Evaluar finalmente el mejor modelo usando el conjunto de prueba.

Tecnologías utilizadas

Python

Pandas

NumPy

Matplotlib

Scikit-learn

Jupyter Notebook / Google Colab

Archivo principal

El desarrollo completo del avance se encuentra en:

AvanceProyecto_final_revisado.ipynb

Ejecución

El notebook puede ejecutarse en Google Colab o en un entorno local de Jupyter.

Al comenzar la ejecución deben estar disponibles los archivos:

tmdb_5000_movies.csv
tmdb_5000_credits.csv

Si se utiliza Google Colab, el notebook permite cargarlos directamente cuando no se encuentran en el entorno.

Este repositorio corresponde al avance del proyecto de la materia Algoritmos de Aprendizaje Automático.
