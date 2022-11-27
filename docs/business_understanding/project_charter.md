# Project Charter

## Business background

* Who is the client, what business domain the client is in.

El E-Commerce es actualmente uno de los canales de venta y compra preferidos por los usuarios. Es una alternativa que promete dejar atrás los sistemas tradicionales de comercio. Las empresas de comercio electrónico están constantemente en la búsqueda de estrategias que les permitan posicionar sus marcas, atraer más clientes y mejorar el rendimiento del negocio. Es en ese escenario, donde los proyectos de ciencia datos se convierten en una vía para conocer los usuarios, entender sus necesidades y condiciones, y complacer sus demandas. 

El comercio electrónico genera una gran cantidad de datos que son un activo para soportar la toma de decisiones dentro de una organización. Entre más conocimiento se tenga de lo que dicen y hacen los consumidores mayor proyección tendrá el negocio. Para ello es importante saber administrar los datos y extraer información de los mismos en pro de enriquecer la experiencia de los clientes. 

Este proyecto se enmarca en el sector de comercio electrónico y tiene como objetivo caracterizar los patrones de compra de los consumidores en Brasil. Nuestro cliente es una multinacional de E-commerce reconocida en Europa y que actualmente está interesada en posicionar su negocio en Latinoamérica, particularmente quiere iniciar su despliegue en Brasil.  

![Captura8](https://user-images.githubusercontent.com/99290509/204110775-491696cd-bc41-4856-b237-610a60d9f428.PNG)


* What business problems are we trying to address?

Somos una empresa consultora que ha sido contratada por esta multinacional para caracterizar los patrones de compra en línea de los consumidores en Brasil. Nuestro objetivo es proporcionar evidencia empírica que le permita a la organización ofrecer experiencias de usuario personalizada en la región, así como diseñar estrategias de atención al cliente y de logística eficaces y adecuadas para los nuevos clientes. 

## Scope
* What data science solutions are we trying to build?

Buscamos aplicar técnicas de visualización de datos, métodos de agrupamiento y procesamiento de lenguaje natural para hacer una caracterización amplia del comportamiento de compra en línea de los brasileños, con el objetivo de generar estrategias de marketing focalizadas en las preferencias del comprador. 

* What will we do?

Vamos estructurar una metodología de ciencia de datos para desarrollar y ejecutar el proyecto. Utilizaremos los datos proporcionados por Olist Store (https://olist.com/pt-br/) para hacer las diferentes implementaciones.  Haremos uso de herramientas de ciencia de datos para hacer una exploración, visualización, preprocesamiento, extracción de características, modelado y evaluación de desempeño de las soluciones propuestas. 


* How is it going to be consumed by the customer?

El servicio va ser consumido por el cliente a través de un dashboard diseñado en Colab.

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
		
		Maira Alejandra Garcia 
		
		
	* Client: Multinacional 
		* Data administrator
		
		Olist Store https://olist.com/pt-br/
		
		* Business contact
		
		Director de proyectos de analítca de la Multinacional 
	
## Metrics

* What are the qualitative objectives? (e.g. reduce user churn)

Mejorar la percepción de los productos por parte de los clientes de la plataforma ecommerce a través de la caracterización del cliente y las revisiones que realizan a los productos. 

* What is a quantifiable metric  (e.g. reduce the fraction of users with 4-week inactivity)

Uno de los principales objetivos es la identificación de productos con críticas negativas y positivas para generar estrategias de marketing para estos productos. Dentro de la información de la base de datos cada producto tiene puntaciones de 1 a 5, lo cual permite realizar una clasificación binaria de esta característica y hacer el análisis requerido. 

Se analizarán los comentarios realizados por los revisores y se implementarán modelos empleando diferentes técnicas de machine learning y deep learning comparando el desempeño de cada uno de los modelos. 

Adicionalmente se realizará un análisis de ventas anual para identificar el crecimiento de venta de los productos y los medios de pago utilizados por los clientes. 

* Quantify what improvement in the values of the metrics are useful for the customer scenario (e.g. reduce the  fraction of users with 4-week inactivity by 20%) 

A partir del análisis realizado, se plantearán estrategias para dar mayor visualización a los productos (priorización de visibilidad). Lo que se espera obtener con esta solución es brindarle herramientas al ecommerce para la toma de decisiones relacionada con la venta de sus productos a partir de la reseña de los clientes.

* What is the baseline (current) value of the metric? (e.g. current fraction of users with 4-week inactivity = 60%)

No se tiene información actual del tiempo que le toma a la multinacional en analizar información y diseñar estrategias. A partir de la implementación de modelos de analítica de datos que permitan predecir la valoración del producto, se pueden establecer las estrategias de visualización y marketing del producto. 

* How will we measure the metric? (e.g. A/B test on a specified subset for a specified period; or comparison of performance after implementation to baseline)

El desempeño que tenga el modelo para realizar la predicción de la valoración del producto. 


## Plan
* Phases (milestones), timeline, short description of what we'll do in each phase.

El proyecto iniciará el 2 de noviembre y finalizará el 9 de diciembre, tiempo durante el cual se realizarán las actividades relacionadas con el entendimiento del negocio, de los datos, preprocesamiento de los datos, modelado, comparación de modelos y despliegue. En la siguiente figura se puede visualizar el cronograma y el diagrama de gantt del proyecto. 

![image](https://user-images.githubusercontent.com/99290509/204110831-ec4bf104-4353-4799-91dd-f3b3bd367b6a.png)


## Architecture
* Data
  * What data do we expect? Raw data in the customer data sources (e.g. on-prem files, SQL, on-prem Hadoop etc.)

El conjunto de datos completo corresponde a 9 tablas en formato de archivo de valores separado por comas (cvs). El archivo zip con estas tablas esta disponible en   la siguiente ruta: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?resource=download

El conjunto de datos se almacena en google drive. Luego se descarga y descomprime en Google Colab. Utilizamos comandos de Linux y python para el manejo de archivos comprimidos y lectura de archivos de valores separados por comas. Para más detalles ver [descarga_file.ipynb](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/docs/data/descarga_file.ipynb)

* What tools and data storage/analytics resources will be used in the solution e.g.,
  
Utilizamos Google Drive como entorno para el almacenamiento de datos de la fuente primaria. El almacenamiento de los datos requiere un espacio de 46.2MB. Además, utilizaremos Github para guardar archivos que se generen en el desarollo de la solución. 
Para el análisis de los datos usamos Python en el ambiente colaborativo de Google (Google Colab). En este entorno de ejecución disponemos de 12.68 GB de RAM, 78.19 GB de Disco y la GPU NVIDIA T4 con la versión del Driver 460.32.03 y CUDA 11.2 respectivamente. El entorno de GPU es recomendable para la eficiencia computacional en la fase de modelamiento.

DEMOS COLOCAR PANTALLAZOS, REVISAR ULTIMOS MINUTOS DE LA ÚLTIMA CLASE: Está ok está?

![image](https://user-images.githubusercontent.com/99290509/204112575-2fa8e48c-1e32-41ed-8061-43d11ebde394.png)

También haremos uso de las siguientes técnicas de machine learning y deep learning: 
- Machine Learning Technique: K Nearest Neighbour, Naive Bayes, Logistic Regression , SVM, Random Forest, gradient Boosting, Decision tree, Model Calibration.
- Deep Learning Technique: Multi-layered Perceptrons, Convolution Neural Networks, LSTM, Underfitting, Overfitting, Probability, Text Processing, Python syntax and data structures, Keras library, etc.

* How will the score or operationalized web service(s) (RRS and/or BES) be consumed in the business workflow of the customer? If applicable, write down pseudo code for the APIs of the web service calls.
  * How will the customer use the model results to make decisions
  * Data movement pipeline in production
  * Make a 1 slide diagram showing the end to end data flow and decision architecture
    * If there is a substantial change in the customer's business workflow, make a before/after diagram showing the data flow.
 
![image](https://user-images.githubusercontent.com/99290509/204114161-ba2c052d-d09d-42b4-8faf-3281af9e94e3.png)


## Communication
* How will we keep in touch? Weekly meetings?

La comunicación será fluida y constante entre el equipo de trabajo, se usarán la metodología ágil Scrum como base para el desarrollo del proyecto. Se definirán sprint para que los miembros del proyecto se reunan cada semana y analicen los avances del proyecto, entregables, tiempo y presupuestos de ejecución, para resolver cualquier imprevisto sujeto a la ejecución del proyecto. Adicionalmente se contará con un tablero en trello que cuente con listas "Por hacer", "En progreso" y "Hecho" donde se registrarán las actividades con su respectivo responsable y fechas límite no solo para realizar seguimiento al proyecto, si no para registrar todas aquellas dudas o sugerencias que puedan mejorar la comunicación del equipo de trabajo. 
	

* Who are the contact persons on both sides?

Equipo del proyecto:

Carolina Luque
Maira García
