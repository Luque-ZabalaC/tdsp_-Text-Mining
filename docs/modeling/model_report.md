# Reporte final del modelo

El modelo de clasificación propuesto permite etiquetar los comentarios de los usuarios según el tipo de sentimiento (negativo o positivo).

## Enfoque analítico
* ¿Cuál es la etiqueta objetivo?

La variable objetivo es la naturaleza del comentario. La etiqueta es 1 si el comentario es positivo y 0 en otro caso.

* ¿Cuáles son las entradas?

La entrada del modelo es la matriz TF-IDF, generada a patir de la matriz de términos documento del corpus preprocesado. 

* ¿Qué tipo de modelo se construyo?

Se contruyo un modelo de clasificación.

## Solution Description
* Simple solution architecture (Data sources, solution components, data flow)
* What is output?

## Data
* Source
* Data Schema
* Sampling
* Selection (dates, segments)
* Stats (counts)

## Features
* List of raw and derived features 
* Importance ranking.

## Algorithm
* Description or images of data flow graph
  * if AzureML, link to:
    * Training experiment
    * Scoring workflow
* What learner(s) were used?
* Learner hyper-parameters

## Results
* ROC/Lift charts, AUC, R^2, MAPE as appropriate
* Performance graphs for parameters sweeps if applicable
