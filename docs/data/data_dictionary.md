# Data Dictionary

La información está contenida en 8 tablas, las cuales se encuentran relacionadas tal como se puede apreciar en el siguiente esquema de la base de datos. 

![image](https://user-images.githubusercontent.com/99290509/204057899-2d0a83aa-4858-44bb-9e4b-f3f02ace49c7.png)

El diagrama entidad relación de la base de datos se visualiza en la siguiente figura, en la cual se pueden identificar las entidades de la base de datos, las relaciones entre ellas, las claves de cada entidad y cada una de sus campos.  

![image](https://user-images.githubusercontent.com/99290509/204058226-bf15dd88-cf14-440d-ba0e-3bacaefa5c0c.png)

A continuación se presenta la descripción de las ocho tablas que conforman la base de datos:

## Tabla 1

olist_orders_dataset: tabla que permite la conexión con las tablas que contienen la información de pagos, reseñas, cliente y artículos. Contiene detalles relacionados con el pedido.


| column | type | description |
| --- | --- | --- |
| order_id | varchar | e481f51cbdc54678b7cc49136f2d6af7 |
| customer_id | varchar | 9ef432eb6251297304e76186b10a928d |
| order_status | varchar | delivered |
| order_purchase_timestamp | date | 2/10/2017  10:56:33 a. m. |
| order_approved_at | date |2/10/2017  11:07:15 a. m. |
| order_delivered_carrier_date | date | 4/10/2017  7:55:00 p. m. |
| order_delivered_customer_date | date |10/10/2017  9:25:13 p. m. |
| order_estimated_delivery_date | date | 18/10/2017  12:00:00 a. m. |





## Table 2

olist_order_items_datase: contiene los detalles del artículo de compra, fecha de envío, el precio, entre otros.


Here you must describe the table

| column | type | description |
| --- | --- | --- |
| col1 | INT | Example column |

## Table 3

olist_order_reviews_dataset: contiene detalles de las reseñas publicadas por el cliente sobre un producto comprado.

## Table 4
olist_products_dataset: contiene detalles de identificación del producto como el ID, categoría y medidas.

## Table 5
olist_order_payments_dataset: contiene los detalles de pago de cada pedido.

## Table 6
olist_customers_dataset: contiene la información de la base de clientes de la firma.

## Table 7
olist_geolocation_dataset: contiene información geográfica de los vendedores y los clientes.

## Table 8
olist_sellers_dataset: contiene información relacionada con los vendedores registrados con la firma.
