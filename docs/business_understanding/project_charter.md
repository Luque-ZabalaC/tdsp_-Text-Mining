# Project Charter

## Business background

* Who is the client, what business domain the client is in.

El E-Commerce es actualmente uno de los canales de venta y compra preferidos por los usuarios. Es una alternativa que promete dejar atrás los sistemas tradicionales de comercio. Las empresas de comercio electrónico están constantemente en la búsqueda de estrategias que les permitan posicionar sus marcas, atraer más clientes y mejorar el rendimiento del negocio. Es en ese escenario, donde los proyectos de ciencia datos se convierten en una vía para conocer los usuarios, entender sus necesidades y condiciones, y complacer sus demandas. 

El comercio electrónico genera una gran cantidad de datos que son un activo para soportar la toma de decisiones dentro de una organización. Entre más conocimiento se tenga de lo que dicen y hacen los consumidores mayor proyección tendrá el negocio. Para ello es importante saber administrar los datos y extraer información de los mismos en pro de enriquecer la experiencia de los clientes. 

Este proyecto se enmarca en el sector de comercio electrónico y tiene como objetivo caracterizar los patrones de compra de los consumidores en Brasil. Nuestro cliente es una multinacional de E-commerce reconocida en Europa y que actualmente está interesada en posicionar su negocio en Latinoamérica, particularmente quiere iniciar su despliegue en Brasil.  

* What business problems are we trying to address?

Somos una empresa consultora que ha sido contratada por esta multinacional para caracterizar los patrones de compra en línea de los consumidores en Brasil. Nuestro objetivo es proporcionar evidencia empírica que le permita a la organización ofrecer experiencias de usuario personalizada en la región, así como diseñar estrategias de atención al cliente y de logística eficaces y adecuadas para los nuevos clientes. 

## Scope
* What data science solutions are we trying to build?

Buscamos aplicar técnicas de visualización de datos, métodos de agrupamiento y procesamiento de lenguaje natural para hacer una caracterización amplia del comportamiento de compra en línea de los brasileños, con el objetivo de generar estrategias de marketing focalizadas en las preferencias del comprador. 

* What will we do?

Vamos estructurar una metodología de ciencia de datos para desarrollar y ejecutar el proyecto. Por otro lado, utilizaremos los datos proporcionados por Olist Store (https://olist.com/pt-br/) para hacer las difernetes implementaciones.  Haremos uso de herramientas de ciencia de datos para hacer una exploración, visualización, preprocesamiento, extracción de características, modelado y evaluación de desempeño de las soluciones propuestas. 


* How is it going to be consumed by the customer?

El servicio va ser consumido por el cliente a través de un dashboard diseñado en Power BI.

## Personnel
* Who are on this project:
	* Microsoft: 
		* Project lead
		
		Maira Alejandra Garcia 
		* Project Management
                
		Carolina Luque                
		* Data scientist(s)
		
		Maira Alejandra Garcia
		Carolina Luque
		* Account manager
		
		Maira alejandra Garcia 
		
		
	* Client: Multinacional 
		* Data administrator
		
		Olist Store https://olist.com/pt-br/
		
		* Business contact
		
		Director de proyectos de analítca de la Multinacional 
	
## Metrics

Identificar productos con críticas negativas y dar mayor visilibilidad a los productos más populares entre los clientes

Dentro de la información se presenta la clasificación del producto con estrellas de 1 a 5, esto permite convertir esta variable en un problema de clasificación binaria tratando las calificaciones de 4 y 5 estrellas como la clase positiva y el resto como la clase negativa.

* What are the qualitative objectives? (e.g. reduce user churn)

 *

* What is a quantifiable metric  (e.g. reduce the fraction of users with 4-week inactivity)
Las matrices de confusión se utilizan para obtener una idea del tipo de errores que comete el modelo. Se requiere precisión para reducir el número de falsos positivos y se necesita recordar para reducir el número de falsos negativos. Esta es la razón por la que utilizaremos la puntuación macro F1 como métrica.

* Quantify what improvement in the values of the metrics are useful for the customer scenario (e.g. reduce the  fraction of users with 4-week inactivity by 20%) 
* What is the baseline (current) value of the metric? (e.g. current fraction of users with 4-week inactivity = 60%)
* How will we measure the metric? (e.g. A/B test on a specified subset for a specified period; or comparison of performance after implementation to baseline)

## Plan
* Phases (milestones), timeline, short description of what we'll do in each phase.

## Architecture
* Data
  * What data do we expect? Raw data in the customer data sources (e.g. on-prem files, SQL, on-prem Hadoop etc.)
* Data movement from on-prem to Azure using ADF or other data movement tools (Azcopy, EventHub etc.) to move either
  * all the data, 
  * after some pre-aggregation on-prem,
  * Sampled data enough for modeling 

* What tools and data storage/analytics resources will be used in the solution e.g.,
  * ASA for stream aggregation
  * HDI/Hive/R/Python for feature construction, aggregation and sampling
  * AzureML for modeling and web service operationalization
* How will the score or operationalized web service(s) (RRS and/or BES) be consumed in the business workflow of the customer? If applicable, write down pseudo code for the APIs of the web service calls.
  * How will the customer use the model results to make decisions
  * Data movement pipeline in production
  * Make a 1 slide diagram showing the end to end data flow and decision architecture
    * If there is a substantial change in the customer's business workflow, make a before/after diagram showing the data flow.

## Communication
* How will we keep in touch? Weekly meetings?
* Who are the contact persons on both sides?
