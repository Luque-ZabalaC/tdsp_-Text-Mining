# Data Dictionary

La información está contenida en 8 tablas, las cuales se encuentran relacionadas tal como se puede apreciar en el siguiente esquema de la base de datos. 

![image](https://user-images.githubusercontent.com/99290509/204057899-2d0a83aa-4858-44bb-9e4b-f3f02ace49c7.png)

El diagrama entidad relación de la base de datos se visualiza en la siguiente figura, en la cual se pueden identificar las entidades de la base de datos, las relaciones entre ellas, las claves de cada entidad y cada una de sus campos.  

![image](https://user-images.githubusercontent.com/99290509/204058226-bf15dd88-cf14-440d-ba0e-3bacaefa5c0c.png)

A continuación se presenta la descripción de las ocho tablas que conforman la base de datos:

## Tabla 1

olist_orders_dataset: tabla que permite la conexión con las tablas que contienen la información de pagos, reseñas, cliente y artículos. Contiene detalles relacionados con el pedido.


| columna | tipo | descripción |
| --- | --- | --- |
| order_id | varchar | e481f51cbdc54678b7cc49136f2d6af7 |
| customer_id | varchar | 9ef432eb6251297304e76186b10a928d |
| order_status | varchar | delivered |
| order_purchase_timestamp | date | 2/10/2017  10:56:33 a. m. |
| order_approved_at | date |2/10/2017  11:07:15 a. m. |
| order_delivered_carrier_date | date | 4/10/2017  7:55:00 p. m. |
| order_delivered_customer_date | date |10/10/2017  9:25:13 p. m. |
| order_estimated_delivery_date | date | 18/10/2017  12:00:00 a. m. |


## Tabla 2

olist_order_items_datase: contiene los detalles del artículo de compra, fecha de envío, el precio, entre otros.

| columna | tipo | descripción |
| --- | --- | --- |
| order_id | varchar | e481f51cbdc54678b7cc49136f2d6af7 |
| order_item_id | int | 1 |
| product_id | varchar | 4244733e06e7ecb4970a6e2683c13e61 |
| seller_id | varchar | 48436dade18ac8b2bce089ec2a041202 |
| shipping_limit_date | varchar | 19/09/2017  9:45:35 a. m. |
| price | float |5890|
| freight_value | float | 1329 |

						
## Tabla 3

olist_order_reviews_dataset: contiene detalles de las reseñas publicadas por el cliente sobre un producto comprado.

| columna | tipo | descripción |
| --- | --- | --- |
| order_id | varchar | 7bc2406110b926393aa56f80a40eba40 |
| review_id | varchar | 73fc7af87114b39712e6da79b0a377eb |
| review_score |int | 4 |
| review_comment_title | varchar |  |
| review_comment_message | varchar | Recebi bem antes do prazo estipulado |
| review_creation_date | varchar | 2018-01-18 00:00:00 |
| review_answer_timestamp | varchar | 2018-01-18 21:46:59 |


## Table 4
olist_products_dataset: contiene detalles de identificación del producto como el ID, categoría y medidas.

| columna | tipo | descripción |
| --- | --- | --- |
| product_id | varchar | 7bc2406110b926393aa56f80a40eba40 |
| product_category_name | varchar | perfumaria	 |
| product_name_lenght |float | 40.0 |
| product_description_lenght | float | 287.0	 |
| product_photos_qty | float | 1.0 |
| product_weight_g | float | 225.0	 |
| product_length_cm | float | 16.0 |
| product_height_cm | float | 10.0 |
| product_width_cm | float | 14.0 |


## Table 5
olist_order_payments_dataset: contiene los detalles de pago de cada pedido.

## Table 6
olist_customers_dataset: contiene la información de la base de clientes de la firma.

## Table 7
olist_geolocation_dataset: contiene información geográfica de los vendedores y los clientes.

## Table 8
olist_sellers_dataset: contiene información relacionada con los vendedores registrados con la firma.
