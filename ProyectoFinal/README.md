# Proyecto Final - Algoritmos de Aprendizaje Automático

## Descripción

Este proyecto desarrolla un modelo de aprendizaje automático para estimar el riesgo comercial de una película, definido como la posibilidad de que no supere su presupuesto de producción mediante los ingresos de taquilla reportados.

El problema se plantea como una clasificación binaria:

- `CommercialRisk = 0`: la película superó su presupuesto.
- `CommercialRisk = 1`: la película no superó su presupuesto.

El objetivo principal es construir una solución reproducible, comparar diferentes familias de modelos y seleccionar una configuración final priorizando especialmente el `recall`, debido al costo de no detectar una película que realmente presenta riesgo comercial.

---

## Dataset

Se utiliza el **TMDB 5000 Movie Dataset**, obtenido de Kaggle.

Archivos principales:

- `tmdb_5000_movies.csv`
- `tmdb_5000_credits.csv`

Fuente:

https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata

Los datos incluyen información como:

- presupuesto,
- duración,
- idioma,
- género,
- compañía productora,
- director,
- guionista,
- actor principal,
- fecha de estreno,
- ingresos de taquilla.

La variable `revenue` se utiliza únicamente para construir la variable objetivo y no se utiliza como predictor para evitar fuga de información.

---

## Variable objetivo

La variable objetivo utilizada es:

```text
CommercialRisk
