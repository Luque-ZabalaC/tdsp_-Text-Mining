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



## Model Understanding

* Variable Importance (significance)

* Insight Derived from the Model

## Conclusion and Discussions for Next Steps

* Conclusion on Feasibility Assessment of the Machine Learning Task

* Discussion on Overfitting (If Applicable)

* What other Features Can Be Generated from the Current Data

* What other Relevant Data Sources Are Available to Help the Modeling
