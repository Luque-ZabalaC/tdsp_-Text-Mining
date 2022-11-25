# Data and Feature Definitions

## Datos públicos de comercio electrónico brasileño por Olist.

El conjunto de datos tiene información de 100k pedidos de 2016 a 2018 realizados en múltiples mercados en Brasil. Prticularmente, se tiene información sobre: el estado del pedido, precio, forma de pago, rendimiento del flete, ubicación del cliente, atributos del producto y las reseñas escritas por los consumidores. También disponemos de un conjunto de datos de geolocalización que relaciona los códigos postales con las coordenadas latitud/longitud.

Los datos estan anonimizados. La denominación de las empresas y socios se han reemplazado con los nombres de las grandes casas de Game of Thrones. El conjunto de datos esta disponible en https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?resource=download&select=olist_customers_dataset.csv. Los datos son proporcionados por Olist, la tienda más grande del mercado brasileño. Olist conecta pequeñas empresas de todo Brasil a los canales sin problemas y con un solo contrato. Esos comerciantes pueden vender sus productos a través de la tienda Olist y enviarlos directamente a los clientes utilizando los socios logísticos de Olist. Después de que un cliente compra el producto, se notifica a un vendedor para cumplir con ese pedido. Una vez que el cliente recibe el producto, o vence la fecha estimada de entrega, el cliente recibe una encuesta de satisfacción por correo electrónico donde puede dejar una nota sobre la experiencia de compra y anotar algunos comentarios.

## Fuentes de datos sin procesar.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky"><span style="font-weight:bold">**Conjunto de datos**</span></th>
    <th class="tg-0pky">*<span style="font-style:italic">*Ubicación original **</span></th>
    <th class="tg-0pky">*<span style="font-style:italic">*Ubicación de destino **</span></th>
    <th class="tg-0pky">*<span style="font-style:italic">*Herramientas/Scripts**</span></th>
    <th class="tg-0pky"><span style="font-weight:bold">**Enlace**</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">olist_orders_dataset</td>
    <td class="tg-0pky">Los datos se descargan manualmente, como archivo zip, con la opción "download" de la   página de Kaggle (), ingresando con usuario registrado. </td>
    <td class="tg-0pky">Los datos se cargan en&nbsp;&nbsp;&nbsp;GoogleDrive (). Luego, el archivo zip se descarga y descomprime en la ruta&nbsp;&nbsp;&nbsp;temporal de GoogleColab: /tmp/archive/</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">olist_order_items_dataset</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">olist_order_reviews_dataset</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">olist_products_dataset</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">olist_order_payments_dataset</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">olist_customers_dataset</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">olist_geolocation_dataset</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">olist_sellers_dataset</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
</tbody>
</table>


| Dataset Name | Original Location   | Destination Location  | Data Movement Tools / Scripts | Link to Report |
| ---:| ---: | ---: | ---: | -----: |
| Dataset 1 | Brief description of its orignal location | Brief description of its destination location | [script1.py](link/to/python/script/file/in/Code) | [Dataset 1 Report](link/to/report1)|
| Dataset 2 | Brief description of its orignal location | Brief description of its destination location | [script2.R](link/to/R/script/file/in/Code) | [Dataset 2 Report](link/to/report2)|

* **olist_orders_dataset**: tabla que permite la conexión con otras 4 tablas. Contiene detalles relacionados con el pedido. 
* **olist_order_items_datase**: contiene los detalles del artículo de compra, fecha de envío, el precio, entre otros.
* **olist_order_reviews_dataset**: contiene detalles de las reseñas publicadas por el cliente sobre un producto comprado.
* **olist_products_dataset**: contiene detalles de identificación del producto como el ID, categoría y medidas.
* **olist_order_payments_dataset**: contiene los detalles de pago de cada pedido.
* **olist_customers_dataset**: contiene la información de la base de clientes de la firma.
* **olist_geolocation_dataset**: contiene información geográfica de los vendedores y los clientes.
* **olist_sellers_dataset**: contiene información relacionada con los vendedores registrados con la firma.

## Processed Data
| Processed Dataset Name | Input Dataset(s)   | Data Processing Tools/Scripts | Link to Report |
| ---:| ---: | ---: | ---: | 
| Processed Dataset 1 | [Dataset1](link/to/dataset1/report), [Dataset2](link/to/dataset2/report) | [Python_Script1.py](link/to/python/script/file/in/Code) | [Processed Dataset 1 Report](link/to/report1)|
| Processed Dataset 2 | [Dataset2](link/to/dataset2/report) |[script2.R](link/to/R/script/file/in/Code) | [Processed Dataset 2 Report](link/to/report2)|
* Processed Data1 summary. <Provide brief summary of the processed data, such as why you want to process data in this way. More detailed information about the processed data should be in the Processed Data1 Report.>
* Processed Data2 summary. <Provide brief summary of the processed data, such as why you want to process data in this way. More detailed information about the processed data should be in the Processed Data2 Report.> 

## Feature Sets

| Feature Set Name | Input Dataset(s)   | Feature Engineering Tools/Scripts | Link to Report |
| ---:| ---: | ---: | ---: | 
| Feature Set 1 | [Dataset1](link/to/dataset1/report), [Processed Dataset2](link/to/dataset2/report) | [R_Script2.R](link/to/R/script/file/in/Code) | [Feature Set1 Report](link/to/report1)|
| Feature Set 2 | [Processed Dataset2](link/to/dataset2/report) |[SQL_Script2.sql](link/to/sql/script/file/in/Code) | [Feature Set2 Report](link/to/report2)|

* Feature Set1 summary. <Provide detailed description of the feature set, such as the meaning of each feature. More detailed information about the feature set should be in the Feature Set1 Report.>
* Feature Set2 summary. <Provide detailed description of the feature set, such as the meaning of each feature. More detailed information about the feature set should be in the Feature Set2 Report.> 
