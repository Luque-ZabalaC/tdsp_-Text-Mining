# Infraestructura

* Configuración basada en el servidor (recursos mínimos del sistema, configuración de VMs, configuración del servidor web, entre otros).

La carga, exploración, preprocesamiento y visualización de los datos así como el entrenamiento, validación y evaluación del modelo se ha realizado usando Google Colaboratory (GoogleColab), con suscripción de ColabPro, para ello se han usado los siguientes recursos:

![image](https://user-images.githubusercontent.com/99290509/205350313-7b6b9f19-89b9-483e-81cc-cb4db8d9600b.png)

Se creó un archivo pickle del modelo entrenado, el cual es usado para crear la API del proyecto. La API se realizó usando Flask, el cual es un framework de Python para el desarrollo de aplicaciones web.  Para la visualización del servicio, se usó Postman. Postman es una plataforma que permite probar la API, ingresando un valor de entrada y visualizando la salida de acuerdo a lo deseado en el proyecto. El objetivo del proyecto es a partir de un comentario del cliente clasificar si es negativo o positivo y el porcentaje de probabilidad. 


* Environment configuration (pyenv, poetry, jupyter, rstudio).

Para el proyecto se realizó una API (API.py) usando Flask con un método POST. Se usa Postman para ingresar el texto que se desea analizar. 

![image](https://user-images.githubusercontent.com/99290509/207174710-f2646ec0-a7df-445b-bb28-23948b2c95cb.png)

* Pipelines de ejecución (airflow, mlflow).

1. py -m venv env
2. env\Scripts\activate
3. Instalaciones
  pip install flask
  pip install pandas
  pip install numpy
  pip install shap
  pip install matplotlib
  pip install seaborn

4. set FLASK_APP=app.py
5. flask run
