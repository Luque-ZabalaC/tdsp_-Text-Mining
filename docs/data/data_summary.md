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

Al analizar cada una de las tablas se puede apreciar que en algunas de ellas hay registros que no tienen información válida, como es el caso de la tabla productos. Para este caso se verifica los valores nulos asociados a las columnas 'product_categoy_name' y 'product_weight_g'. 

```python
olist_products[olist_products['product_category_name'].isnull() == True]
```
Estos son algunos de los 610 registros que presentan información nula relacionada con el nombre de la categoría del producto. 
|index|product\_id|product\_category\_name|product\_name\_lenght|product\_description\_lenght|product\_photos\_qty|product\_weight\_g|product\_length\_cm|product\_height\_cm|product\_width\_cm|
|---|---|---|---|---|---|---|---|---|---|
|105|a41e356c76fab66334f36de622ecbd3a|NaN|NaN|NaN|NaN|650\.0|17\.0|14\.0|12\.0|
|128|d8dee61c2034d6d075997acef1870e9b|NaN|NaN|NaN|NaN|300\.0|16\.0|7\.0|20\.0|
|145|56139431d72cd51f19eb9f7dae4d1617|NaN|NaN|NaN|NaN|200\.0|20\.0|20\.0|20\.0|
|154|46b48281eb6d663ced748f324108c733|NaN|NaN|NaN|NaN|18500\.0|41\.0|30\.0|41\.0|
|197|5fb61f482620cb672f5e586bb132eae9|NaN|NaN|NaN|NaN|300\.0|35\.0|7\.0|12\.0|
|244|e10758160da97891c2fdcbc35f0f031d|NaN|NaN|NaN|NaN|2200\.0|16\.0|2\.0|11\.0|
|294|39e3b9b12cd0bf8ee681bbc1c130feb5|NaN|NaN|NaN|NaN|300\.0|16\.0|7\.0|11\.0|
|299|794de06c32a626a5692ff50e4985d36f|NaN|NaN|NaN|NaN|300\.0|18\.0|8\.0|14\.0|
|347|7af3e2da474486a3519b0cba9dea8ad9|NaN|NaN|NaN|NaN|200\.0|22\.0|14\.0|14\.0|
|428|629beb8e7317703dcc5f35b5463fd20e|NaN|NaN|NaN|NaN|1400\.0|25\.0|25\.0|25\.0|
|436|3a78f64aac654298e4b9aff32fc21818|NaN|NaN|NaN|NaN|4300\.0|30\.0|10\.0|48\.0|
|459|bcb815bba008d89458e428078c0b9211|NaN|NaN|NaN|NaN|150\.0|16\.0|2\.0|11\.0|
|504|6b82874c6b51b92913dcdb364eaaae0f|NaN|NaN|NaN|NaN|21450\.0|70\.0|34\.0|50\.0|
|514|c68b419d9c6038271b85bac98adb0fc9|NaN|NaN|NaN|NaN|1000\.0|16\.0|14\.0|30\.0|
|552|1dcd65bb5dd967d7b4c6b0223cefb838|NaN|NaN|NaN|NaN|9150\.0|33\.0|30\.0|44\.0|
|616|671446e8e3aa3df1eca47b6c354a2921|NaN|NaN|NaN|NaN|5500\.0|33\.0|22\.0|33\.0|
|627|f0ea71b6e2ab4cb3bd8f5ba522a25a56|NaN|NaN|NaN|NaN|1300\.0|30\.0|20\.0|30\.0|


```python
olist_products[olist_products['product_weight_g'].isnull() == True]
```
|index|product\_id|product\_category\_name|product\_name\_lenght|product\_description\_lenght|product\_photos\_qty|product\_weight\_g|product\_length\_cm|product\_height\_cm|product\_width\_cm|
|---|---|---|---|---|---|---|---|---|---|
|8578|09ff539a621711667c43eba6a3bd8466|bebes|60\.0|865\.0|3\.0|NaN|NaN|NaN|NaN|
|18851|5eb564652db742ff8f28759cd8d2652a|NaN|NaN|NaN|NaN|NaN|NaN|NaN|NaN|


Se procede a eliminar las filas de valores nulos, es importante tener en cuenta que son 610 registros, lo cual no es significativo respecto al total de entradas totales (32951).

```python
olist_products = olist_products.dropna()  
olist_products.isnull().sum()
```

En la siguiente gráfica comprobamos la distribución de la columna product_weight_g

```python
sns.distplot(olist_products['product_weight_g'])
```
![image](https://user-images.githubusercontent.com/99290509/205499700-24078508-ebed-4a32-950e-34a73a9d92b8.png)

Este procedimiento se realiza con todas las tablas y se verifica la calidad de los datos. Otra de las variables a analizar es la latitud y longitud de los compradores, para verificar que la información sea consistente con la geolocalización de Brasil. Para ello se visualizaron los datos de geolocalización a través de un mapa. 

```python
lat = olist_geolocation['geolocation_lat']
lon = olist_geolocation['geolocation_lng']

plt.figure(figsize=(18,18))

m = Basemap()
#dibuja un límite alrededor del mapa, rellena el fondo.
# este fondo terminará siendo el color del océano, ya que
# los continentes se dibujarán en la parte superior.
m.drawmapboundary(fill_color='#46bcec')
# fill continents, establece el color del lago igual que el color del océano.
m.fillcontinents(color='#f2f2f2', lake_color='#46bcec')
# dibuja los límites de los países
m.drawcountries()
# dibuja puntos con marcadores
m.scatter(lon, lat, zorder=10, alpha=0.8, color='#009c3b')
# Se establece el título de la figura
plt.title(label='Geolocalización - Comercio electrónico Brasileño -Olist', fontsize=20)
plt.show()
```
![image](https://user-images.githubusercontent.com/99290509/205499830-7e8b8d12-0082-46a0-b1b0-d92671fe36ae.png)

En la gráfica se visualizan puntos ubicados en zonas geográficas diferentes a Brasil, la cual es nuestra región de interés, por lo tanto se remueven los registros que contienen observaciones fuera de dicha región.

```python
# El punto más septentrional de Brasil está a 5 grados 16′ 27,8″ de latitud norte.
olist_geolocation = olist_geolocation[olist_geolocation.geolocation_lat <= 5.27438888]
# El punto más occidental de Brasil está a 73 grados, 58′ 58.19″W Long
olist_geolocation = olist_geolocation[olist_geolocation.geolocation_lng >= -73.98283055]
# El punto más al sur de Brasil está a 33 grados, 45′ 04.21″ S Latitud
olist_geolocation = olist_geolocation[olist_geolocation.geolocation_lat >= -33.75116944]
# El lugar más oriental de Brasil es 34 grados, 47 ′ 35.33 ″ W Long.
olist_geolocation = olist_geolocation[olist_geolocation.geolocation_lng <=  -34.79314722]
```

Al visualizar nuevamente el mapa, se observa que ahora solo se tienen los puntos de región de interés. 

![image](https://user-images.githubusercontent.com/99290509/205499905-9496f8a8-94d6-424e-b5b0-72c6c454c8f1.png)

## Exploración de los datos

Explorando las reseñas de la base de datos, el 76.68% corresponden a reseñas positivas. 

![image](https://user-images.githubusercontent.com/99290509/205500016-b7137812-91ef-4fee-8b63-6f3bcba90063.png)

En la siguiente imagen se visualizan el top de productos más vendidos.

![image](https://user-images.githubusercontent.com/99290509/205500089-348a879d-274a-4854-9f3f-3f945753869e.png)

Los principales medios de pago usados por los compradores son:

![image](https://user-images.githubusercontent.com/99290509/205500142-780a9062-45c7-4197-9a07-e07d8de18195.png)




## Variable Objetivo

## Variables individuales

## Clasificación de las variables

## Relación entre las variables explicativas y la variable objetivo

