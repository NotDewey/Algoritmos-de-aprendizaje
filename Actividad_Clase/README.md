# Clasificación de Vinos con Machine Learning

Este proyecto implementa un modelo de **clasificación de vinos** utilizando el dataset `Wine` de `scikit-learn`.

El objetivo es entrenar un modelo capaz de clasificar los registros en tres clases didácticas:

- Cabernet
- Merlot
- Pinot Noir

> Estas etiquetas se utilizan únicamente con fines didácticos y no corresponden a variedades reales identificadas por el dataset original.

## Tecnologías utilizadas

- Python
- Pandas
- Matplotlib
- Scikit-learn
- Joblib

## Características utilizadas

El modelo utiliza únicamente las siguientes variables:

- `alcohol`
- `malic_acid`
- `color_intensity`
- `proline`

## Preparación de los datos

El dataset se divide en:

- 80% para entrenamiento
- 20% para prueba
- `random_state = 42`
- División estratificada utilizando la variable objetivo

Esto permite conservar una proporción similar de cada clase en los conjuntos de entrenamiento y prueba.

## Modelo

Se utiliza un `Pipeline` compuesto por:

1. `StandardScaler`
2. `SVC` con kernel lineal

```python
modelo = Pipeline([
    ("scaler", StandardScaler()),
    ("svm", SVC(kernel="linear"))
])
