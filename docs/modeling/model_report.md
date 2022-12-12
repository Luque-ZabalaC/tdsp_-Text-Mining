# Reporte final del modelo

El modelo de clasificación propuesto permite etiquetar los comentarios de los usuarios según el tipo de sentimiento (negativo o positivo).

## Enfoque analítico
* ¿Cuál es la etiqueta objetivo?

La variable objetivo es la naturaleza del comentario. La etiqueta es 1 si el comentario es positivo y 0 en otro caso.

* ¿Cuáles son las entradas?

La entrada del modelo es la matriz TF-IDF, generada a patir de la matriz de términos documento del corpus preprocesado. 

* ¿Qué tipo de modelo se construyo?

Se contruyo un modelo de clasificación.

## Descripción de la solución

Proponemos dos modelos de clasificación: regresión logistica y Naive Bayes.

## Data

Para más detalles a cerca de los datos ver  [data](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/tree/master/docs/data).

## Extracción de características 

```python
def extract_features_from_corpus(corpus, vectorizer, df=False):
    """
    Args
    ------------
    text: text to be transformed into a document-term matrix [type: string]
    vectorizer: engine to be used in the transformation [type: object]
    """
    
    # Extracting features
    corpus_features = vectorizer.fit_transform(corpus).toarray()
    features_names = vectorizer.get_feature_names()
    
    # Transforming into a dataframe to give interpetability to the process
    df_corpus_features = None
    if df:
        df_corpus_features = pd.DataFrame(corpus_features, columns=features_names)
    
    return corpus_features, df_corpus_features
    
# Creating an object for the CountVectorizer class
count_vectorizer = CountVectorizer(max_features=300, min_df=7, max_df=0.8, stop_words=pt_stopwords)

# Extracting features for the corpus
countv_features, df_countv_features = extract_features_from_corpus(reviews_stemmer, count_vectorizer, df=True)
print(f'Shape of countv_features matrix: {countv_features.shape}\n')
print(f'Example of DataFrame of corpus features:')
df_countv_features.head()

# Creating an object for the CountVectorizer class
tfidf_vectorizer = TfidfVectorizer(max_features=300, min_df=7, max_df=0.8, stop_words=pt_stopwords)

# Extracting features for the corpus
tfidf_features, df_tfidf_features = extract_features_from_corpus(reviews_stemmer, tfidf_vectorizer, df=True)
print(f'Shape of tfidf_features matrix: {tfidf_features.shape}\n')
print(f'Example of DataFrame of corpus features:')
df_tfidf_features.head()
```


## Algoritmo
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

## Resultados

![image](https://user-images.githubusercontent.com/81445104/207159970-d84d81db-df87-470b-8934-591bbba895fd.png)

