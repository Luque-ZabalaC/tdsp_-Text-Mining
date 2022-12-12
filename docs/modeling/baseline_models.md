# Informe del modelo de referencia

Para la clasificación y análisis de sentimientos de los usiarios utilizamos dos modelos: modelo de regresión logística y Naive Bayes. 

## Enfoque analítico
* ¿Cuál es la etiqueta objetivo?

La variable objetivo es la naturaleza del comentario. La etiqueta es 1 si el comentario es positivo y 0 en otro caso.

* ¿Cuáles son las entradas?

La entrada del modelo es la matriz TF-IDF, generada a patir de la matriz de términos documento del corpus preprocesado. 

* ¿Qué tipo de modelo se construyo?

Se contruyo un modelo de clasificación.

## Descripción del modelo

* Modelos y parámetros.

A continuación se muestra la estructura de los modelos 

```python
# Logistic Regression hyperparameters
logreg_param_grid = {
    'C': np.linspace(0.1, 10, 20),
    'penalty': ['l1', 'l2'],
    'class_weight': ['balanced', None],
    'random_state': [42],
    'solver': ['liblinear']
}

# Setting up the classifiers
set_classifiers = {
    'LogisticRegression': {
        'model': LogisticRegression(),
        'params': logreg_param_grid
    },
    'Naive Bayes': {
        'model': GaussianNB(),
        'params': {}
    }
}
```

## Resultados y desempeño del modelo

![image](https://user-images.githubusercontent.com/81445104/207119306-8ab6490b-fa1e-46d6-92ee-7b6473353ad6.png)

![image](https://user-images.githubusercontent.com/81445104/207119741-406e424d-e799-4def-86ad-6ddd9040398d.png)


## Entendimiento del modelo

El modelo permite ingresar un comentario y determinar el porcentaje de positividad o negatividad del mismo.

![image](https://user-images.githubusercontent.com/81445104/207148459-440f9247-fe37-498d-aec6-16de28c567e9.png)


![image](https://user-images.githubusercontent.com/81445104/207148508-1f0b0b26-57d7-44fe-af19-4be490fd6858.png)


## Conclusión y discusión

* El modelo Naive Bayes muestra una mejor precisión frente al modelo de regresión logistica. Las demás métricas muestran un mejor desempeño para el modelo de regresión logística.

* En estudios futuros se podría plantear un modelo con una variable respuesta que contemple más categorías.

* Sería de utilidad incorporar un análisis por región y considerando otras covariabls de los usuarios. Por ejemplo, ingresos.
