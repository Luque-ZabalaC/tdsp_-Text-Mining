# Definición de datos y características.

## Datos públicos de comercio electrónico brasileño por Olist.

El conjunto de datos tiene información de 100k de pedidos de 2016 a 2018 realizados en múltiples mercados en Brasil. Particularmente, se tiene información sobre: el estado del pedido, precio, forma de pago, rendimiento del flete, ubicación del cliente, atributos del producto y las reseñas escritas por los consumidores. También disponemos de un conjunto de datos de geolocalización que relaciona los códigos postales con las coordenadas latitud/longitud.

Los datos estan anonimizados. La denominación de las empresas y socios se han reemplazado con los nombres de las grandes casas de Game of Thrones. El conjunto de datos esta disponible en [Kaggle_Olist](https://acortar.link/b20WXx).
Los datos son proporcionados por Olist, la tienda más grande del mercado brasileño. Olist conecta pequeñas empresas de todo Brasil a los canales sin problemas y con un solo contrato. Esos comerciantes pueden vender sus productos a través de la tienda Olist y enviarlos directamente a los clientes utilizando los socios logísticos de Olist. Después de que un cliente compra el producto, se notifica a un vendedor para cumplir con ese pedido. Una vez que el cliente recibe el producto, o vence la fecha estimada de entrega, el cliente recibe una encuesta de satisfacción por correo electrónico donde puede dejar una nota sobre la experiencia de compra y anotar algunos comentarios.

## Fuentes de datos sin procesar.

| **Conjunto de datos** | **Ubicación original**                                                                                                                           | **Ubicación de destino**                                                                                                                    | **Herramientas/Scripts** | **Enlace** |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|------------|
| archive.zip           | Los datos se descargan manualmente, como archivo zip, con la opción "download" de la página de Kaggle [Kaggle_Olist](https://acortar.link/b20WXx), ingresando con usuario registrado.  | Los datos se cargan en [GoogleDrive](https://drive.google.com/file/d/1AptgDKWFzgqUn-5YipS3tR09bfg9UVFY/view?usp=share_link). Luego, el archivo zip se descarga y descomprime en Google Colab | [descarga_file.ipynb](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/docs/data/descarga_file.ipynb)                    | [Dataset](https://drive.google.com/file/d/1AptgDKWFzgqUn-5YipS3tR09bfg9UVFY/view?usp=share_link)       |

El **archive.zip** contine los siguientes conjuntos de datos: 

* **olist_orders_dataset**: tabla que permite la conexión con otras 4 tablas. Contiene detalles relacionados con el pedido. 
* **olist_order_items_datase**: contiene los detalles del artículo de compra, fecha de envío, el precio, entre otros.
* **olist_order_reviews_dataset**: contiene detalles de las reseñas publicadas por el cliente sobre un producto comprado.
* **olist_products_dataset**: contiene detalles de identificación del producto como el ID, categoría y medidas.
* **olist_order_payments_dataset**: contiene los detalles de pago de cada pedido.
* **olist_customers_dataset**: contiene la información de la base de clientes de la firma.
* **olist_geolocation_dataset**: contiene información geográfica de los vendedores y los clientes.
* **olist_sellers_dataset**: contiene información relacionada con los vendedores registrados con la firma.

## Datos procesados
| **Conjunto de datos** | **Ubicación**   | **Herramientas procesamiento/Scripts** | **Enlace** |
| ---:| ---: | ---: | ---: | 
| text_prep.csv | [Corpus final](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/scripts/preprocessing/text_prep.csv) | [prep_y_extrac.ipynb](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/scripts/preprocessing/prep_y_extrac.ipynb) | [Reporte](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/tree/master/scripts/preprocessing)|

* **text_prep.csv**: contiene los comentarios originales, los comentarios preprocesados y la puntuación de cada uno. Este es el insumo para la extracción de las características.


## Conjuntos de características

| **Conjunto de datos** | **Ubicación**   | **Herramientas ingeniería características/Scripts** | **Enlace** |
| ---:| ---: | ---: | ---: | 
| train.zip, test.zip | [train](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/scripts/preprocessing/train.zip), [test](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/scripts/preprocessing/test.zip) | [prep_y_extrac.ipynb](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/scripts/preprocessing/prep_y_extrac.ipynb) | [Reporte](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/tree/master/scripts/preprocessing)|

* **train.zip y test.zip**: contiene los conjunto de entrenamiento y prueba. Estos se generan luego de la extracción de las características del conjunto de datos. Se determinó la matriz de términos-documento y la estadística TF-IDF. También se etiquetaron los comentarios a partir de las puntuaciones.
