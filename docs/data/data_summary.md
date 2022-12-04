# Informe de datos

## Resumen general de los datos

El conjunto de datos tiene información de 100k de pedidos de 2016 a 2018 realizados en múltiples mercados en Brasil. Particularmente, y se encuentra disponible en [Kaggle_Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?resource=download&select=olist_customers_dataset.csv). La base de datos contiene 8 tablas (archivos csv) relacionadas entre sí, que tiene información sobre: el estado del pedido, precio, forma de pago, rendimiento del flete, ubicación del cliente, atributos del producto y las reseñas escritas por los consumidores. También disponemos de un conjunto de datos de geolocalización que relaciona los códigos postales con las coordenadas latitud/longitud. 

Para la exploración, análisis y visualización de los datos se requiere la instalación de las siguientes librerías:

```python
>>> !apt-get install libgeos-dev
!pip install pyproj==1.9.6
!pip install fasttext
!python -m spacy download pt
!pip install tensorflow_addons
!pip install basemap
```

Y la importación de las siguientes librerías

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
import spacy
import regex as re
from datetime import datetime
from tqdm import tqdm
import pickle
import scipy
from mpl_toolkits.basemap import Basemap
from sklearn.decomposition import TruncatedSVD
from sklearn.model_selection import train_test_split, RandomizedSearchCV
from sklearn.preprocessing import OneHotEncoder, MinMaxScaler, OrdinalEncoder, StandardScaler
from sklearn.linear_model import LogisticRegression, SGDClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.calibration import CalibratedClassifierCV
from sklearn.metrics import confusion_matrix, accuracy_score, f1_score, log_loss
import fasttext.util
import warnings
from tensorflow_addons.metrics import F1Score
from sklearn.utils.extmath import randomized_svd
from tensorflow.keras.models import Model
from tensorflow.keras.layers import Input, Dense, BatchNormalization, Dropout, Embedding, LSTM, Flatten, Concatenate, Reshape, Conv1D
from tensorflow.keras.optimizers import Adam
from tensorflow.keras.callbacks import ReduceLROnPlateau, ModelCheckpoint
from tensorflow.keras.preprocessing.text import Tokenizer
from tensorflow.keras.preprocessing.sequence import pad_sequences
from tensorflow.keras.regularizers import l2
from xgboost import XGBClassifier
from prettytable import PrettyTable
from keras.models import load_model
from sklearn.metrics import plot_confusion_matrix
```

Los datos fueron descargados desde [Kaggle_Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?resource=download&select=olist_customers_dataset.csv) y alojados en una carpeta en el Drive. Para realizar el cargo de los datos de las 8 tablas se realiza el siguiente proceso:

```python
#Acceso al drive
from google.colab import drive
drive.mount('/content/drive/')
```

```python
# Establecimiento del directorio
raw_path ='/content/drive/MyDrive/Colab Notebooks/06_MetodologiasAgiles/Project/output_folder/'
# Cargue de cada tabla
olist_customer = pd.read_csv(raw_path + 'olist_customers_dataset.csv')
olist_geolocation = pd.read_csv(raw_path + 'olist_geolocation_dataset.csv')
olist_orders = pd.read_csv(raw_path + 'olist_orders_dataset.csv')
olist_order_items = pd.read_csv(raw_path + 'olist_order_items_dataset.csv')
olist_order_payments = pd.read_csv(raw_path + 'olist_order_payments_dataset.csv')
olist_order_reviews = pd.read_csv(raw_path + 'olist_order_reviews_dataset.csv')
olist_products = pd.read_csv(raw_path + 'olist_products_dataset.csv')
olist_sellers = pd.read_csv(raw_path + 'olist_sellers_dataset.csv')
```


## Resumen general de la calidad de los datos

    


## Variable Objetivo

## Variables individuales

## Claseificación de las variables

## Relación entre las variables explicativas y la variable objetivo

