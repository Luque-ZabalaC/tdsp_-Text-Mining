# Deployment


## **Descripción**

El despliegue del proyecto se realizó mediante una [API](https://github.com/Luque-ZabalaC/tdsp_E-Commerce/blob/master/API.py) que usa Flask para generar el servicio web. La API carga el modelo entrenado (archivo pkl). 

En la siguiente figura se puede visualizar la parte inicial del código. La API incluye el código requerido para que a partir de los datos de entrada ingresados por el usuario y el modelo entrenado, se realice la clasificación de sentimientos y determine el porcentaje de probabilidad asociado a la clasificación. 

![image](https://user-images.githubusercontent.com/99290509/207456036-5e04c97d-e128-4523-9175-46af0f654209.png)

Como datos de entrada, la API recibe la reseña que el cliente realiza al producto. La reseña debe estar en idioma portugues, ya que el modelo está entrenado para este idioma. 

![image](https://user-images.githubusercontent.com/99290509/207458630-d15cae04-a8b8-44a4-9c44-2505cd252a70.png)


## **Despliegue de la API**

La API se desplegó usando un servidor local, a través de la interfaz gráfica de la plataforma Postman se realizó un request POST al servidor local, ingresando el texto que se desea analizar que en este caso es la reseña del cliente.  

Los principales pasos requeridos para realizar el despliegue son:

1. Crear el servicio web a través de la API usando Flask
2. Crear el entorno virtual de Flask py -m venv env
3. Activar el entorno virtual env\Scripts\activate
4. Realizar la instalación de las librerías requeridas para el despliegue de la API
5. Ejecutar la API flask run

![image](https://user-images.githubusercontent.com/99290509/207203430-b5283da4-8fa2-4ef0-8881-3fcfd9910644.png)

6. Al copiar la dirección del servidor local en un navegador, podemos observar que el servicio se está ejecutando. 

![image](https://user-images.githubusercontent.com/99290509/207203448-2f553c86-e195-47df-9025-cd7d9381822d.png)
7. Los datos de entrada y las peticiones a la API se realizan haciendo uso de Postman. 

Las siguientes tres imágenes permiten visualizar tres reseñas y la respectiva clasificación realizadas por la API. El primer caso corresponde a una clasificación negativa con un alto porcentaje de probabilidad en esa clasificación. La segunda reseña analizada arroja una clasificación positiva con un porcentaje de probabilidad mucho mayor que la última imagen. 

![image](https://user-images.githubusercontent.com/99290509/207203355-5c8ada12-ae04-462c-8786-d0a733470e32.png)

![image](https://user-images.githubusercontent.com/99290509/207203825-2de0dfc2-9581-4918-b0e3-3d0f2f9f6064.png)

![image](https://user-images.githubusercontent.com/99290509/207203992-4313993b-9bc2-4784-801d-d3b4d12cedb0.png)

