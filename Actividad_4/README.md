# Actividad 4 — Redes Neuronales con `make_moons`

## Descripción

En esta actividad se desarrolla una **red neuronal para un problema de clasificación binaria** utilizando el dataset `make_moons` de Scikit-learn.

El objetivo es realizar el proceso completo de construcción de un modelo de aprendizaje automático: generar y explorar los datos, preparar los conjuntos de entrenamiento y prueba, escalar las variables, construir y entrenar una red neuronal, evaluar su desempeño y visualizar cómo aprende a separar las dos clases.

---

## Objetivo

Construir una red neuronal capaz de clasificar correctamente las observaciones del dataset `make_moons`, analizando su proceso de entrenamiento mediante diferentes métricas y visualizaciones.

Además, se busca comprender:

* Cómo preparar los datos antes de entrenar una red neuronal.
* Cómo funcionan las capas ocultas de una red neuronal.
* Cómo evaluar un modelo de clasificación.
* Cómo detectar posibles señales de sobreajuste.
* Cómo interpretar una matriz de confusión.
* Cómo visualizar una frontera de decisión.
* Cómo afecta el cambio del umbral de clasificación a las métricas del modelo.

---

## Dataset

Se utiliza el dataset artificial `make_moons`, disponible en la librería **Scikit-learn**.

El dataset contiene:

* **1,000 observaciones**
* **2 variables predictoras:** `x1` y `x2`
* **Variable objetivo:** `clase`
* **2 clases:** `0` y `1`
* `noise = 0.20`
* `random_state = 42`

Los datos forman dos grupos con forma de **lunas entrelazadas**, por lo que el problema no puede resolverse correctamente utilizando únicamente una separación lineal.

---

## Librerías utilizadas

La actividad utiliza las siguientes librerías:

```python
numpy
pandas
matplotlib
tensorflow
scikit-learn
```

También se utilizan herramientas específicas como:

```python
make_moons
train_test_split
StandardScaler
accuracy_score
precision_score
recall_score
f1_score
confusion_matrix
Sequential
Dense
EarlyStopping
```

---

## Desarrollo de la actividad

La actividad se divide en los siguientes pasos:

1. Importar librerías y fijar semillas.
2. Crear el dataset.
3. Explorar los datos.
4. Visualizar el problema.
5. Separar entrenamiento y prueba.
6. Escalar los datos.
7. Construir la red neuronal.
8. Compilar el modelo.
9. Entrenar la red.
10. Analizar el aprendizaje.
11. Generar probabilidades y predicciones.
12. Calcular métricas.
13. Generar la matriz de confusión.
14. Visualizar la frontera de decisión.
15. Comparar diferentes umbrales.

---

## Preparación de los datos

Los datos se dividen en:

* **80 % para entrenamiento**
* **20 % para prueba**

Se utiliza:

```python
random_state=42
stratify=y
```

La estratificación permite conservar aproximadamente la misma proporción de las clases `0` y `1` en los conjuntos de entrenamiento y prueba.

---

## Escalamiento

Las variables `x1` y `x2` se normalizan utilizando:

```python
StandardScaler()
```

El escalador se ajusta únicamente utilizando el conjunto de entrenamiento:

```python
scaler.fit_transform(X_train)
```

Posteriormente se utiliza para transformar el conjunto de prueba:

```python
scaler.transform(X_test)
```

Esto evita que información del conjunto de prueba influya durante la preparación del modelo, reduciendo el riesgo de **data leakage**.

---

## Arquitectura de la red neuronal

Se utiliza una red neuronal secuencial con la siguiente arquitectura:

```text
Entrada
  ↓
2 variables
  ↓
Dense — 8 neuronas — ReLU
  ↓
Dense — 4 neuronas — ReLU
  ↓
Dense — 1 neurona — Sigmoid
  ↓
Probabilidad de clase 1
```

En TensorFlow:

```python
model = Sequential([
    Input(shape=(2,)),
    Dense(8, activation="relu"),
    Dense(4, activation="relu"),
    Dense(1, activation="sigmoid")
])
```

Las capas ocultas y la función de activación **ReLU** permiten que la red aprenda relaciones no lineales.

La última capa utiliza **Sigmoid**, produciendo un valor entre `0` y `1` que puede interpretarse como la probabilidad de pertenecer a la clase 1.

---

## Compilación

El modelo se compila utilizando:

```python
optimizer="adam"
loss="binary_crossentropy"
metrics=["accuracy"]
```

### Adam

Se encarga de actualizar los pesos de la red durante el entrenamiento.

### Binary Crossentropy

Mide el error entre las predicciones realizadas por la red y las clases reales en un problema de clasificación binaria.

### Accuracy

Mide la proporción total de predicciones correctas.

---

## Entrenamiento

El modelo puede entrenarse durante un máximo de:

```text
100 épocas
```

con:

```text
Batch size = 32
Validation split = 20 %
```

También se utiliza `EarlyStopping`:

```python
EarlyStopping(
    monitor="val_loss",
    patience=10,
    restore_best_weights=True
)
```

Esto permite detener automáticamente el entrenamiento si la pérdida de validación deja de mejorar durante varias épocas.

Durante cada época se realiza:

1. **Forward pass:** se calcula una predicción.
2. **Cálculo de pérdida:** se mide el error.
3. **Backpropagation:** se calcula la contribución de cada peso al error.
4. **Actualización:** Adam modifica los pesos de la red.

---

## Evaluación del entrenamiento

Se generan gráficas
