# Proyecto de Practica
En este repositorio esta contenido toda la información relevante del proyecto de práctica. El objetivo del proyecto fue realizar un taller interactivo en el cual una persona pueda aplicar los conocimientos obtenidos tras realizar el learning path de Data Engineering de Perficient. 
Se podrán aplicar conocimientos en temas tales como:
Python
* Google Cloud Platform
  * Cloud Dataflow
  * BigQuery
  * Pubsub
  * Permisos
  * Manejo de Costos
* SQL
* Apache Beam

## Taller ##
### SQL ###
Antes de comenzar con el taller propuesto, recomiendo hacer los siguientes ejercicios de SQL como un calentamiento.
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_select1 
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_where1 
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_null1 
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_functions1 
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_wildcards1 
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_in1 
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_join1 
* https://www.w3schools.com/sql/exercise.asp?filename=exercise_groupby1 

### Ejercicio de taxis de Nueva York ###
Para este ejericicio se tomó el dataset en streaming que se tiene acerca de la información de los Taxis amarillos de Nueva York. Si desea conocer más acerca de este dataset, puede seguir este víncullo: https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page.

Para la primera parte del ejercicio, se desea consumir dicho stream de datos usando Apache Beam y Google Cloud Dataflow.
  * Pasos preliminares
    * Instalar **Python 3.7.8** *(Si se instala una versión más reciente, se corre el riesgo de que no sea compatible con Apache Beam)*
      * https://www.python.org/downloads/release/python-378/
    * Instalar Java 8
      * https://www.java.com/es/download/ie_manual.jsp
    * Crear cuenta gratuita de GCP
      * https://k21academy.com/google-cloud/create-google-cloud-free-tier-account/
    * Instalar Google Cloud SDK
      * https://cloud.google.com/sdk/docs/install
    * Configurar Google Cloud SDK
      *  `gcloud init` 
      *  Seleccionar la opcion 1
      *  Seleccionar la cuenta que esta registrada en GCP
      *  Seleccionar el proyecto
      *  No seleccionar region
    * Seguir el siguiente tutorial para la activacion de la cuenta de GCP https://cloud.google.com/docs/authentication/getting-started#windows
      * `TIP` Cuando se tenga que crear la variable de entorno, lo mejor es crearla de forma manual.
       * ![image](https://user-images.githubusercontent.com/35697253/146488498-2ac18e38-4403-4252-a698-6d7393db423b.png)
       * <img width="308" alt="image" src="https://user-images.githubusercontent.com/35697253/146488572-9a4bba6b-cabb-4524-aed6-3c7879f4cc8b.png">
       * <img width="432" alt="image" src="https://user-images.githubusercontent.com/35697253/146488794-08dc8a1b-9b94-4290-80fc-1f6bb07b3f12.png">
       * ![image](https://user-images.githubusercontent.com/35697253/146488950-55c36d27-402a-42bf-89f8-29382a37910f.png)
      * `TIP` Cerrar sesión o reiniciar el computador
    * Como preferencia propia, recomiendo instalar PyCharm como IDE de Python.
    * Instalar los siguientes modulos de python con pip
      * `pip install google-cloud`
      * `pip install google-cloud-storage`
      * `pip install google-cloud-pubsub`
      * `pip install google-cloud-bigquery`
      * `pip install google-cloud-bigquery-storage`
      * `pip install google-apitools`
      * `pip install apache-beam`
      * `pip install 'apache-beam[gcp]'`

Tras haber completado los pasos de preparación, se puede proceder con el ejercicio.
#### Enunciado Parte 1 ####
Se desea ingestar información en tiempo real acerca de los viajes realizados en algunos Taxis de la ciudad de Nueva York para que estos sean analizados posteriormente. Usted debe consumir los datos que estan publicados en Google PubSub y almacenarlos en una base de datos en BigQuery usando Apache Beam con Python. El Topid de pubsub donde esta el stream es : `projects/pubsub-public-data/topics/taxirides-realtime`

Lo ideal es que intente hacer esto sin usar las respuestas a continuación.
#### Paso a paso ####
 * Ir a pubsub y crear una sucripción al topic `projects/pubsub-public-data/topics/taxirides-realtime`
  * <img width="380" alt="image" src="https://user-images.githubusercontent.com/35697253/146497073-e733bbeb-0a37-4adf-8fa0-e06a29a5a11d.png">
  * ![image](https://user-images.githubusercontent.com/35697253/146497217-d08edbec-5f71-491a-9345-121f3ae8a160.png)
 * Crear la tabla en BigQuery con el esquema de datos
  * <img width="262" alt="image" src="https://user-images.githubusercontent.com/35697253/146497776-d20977ce-279f-4c12-94c0-c84d15f07303.png">
 * Crear script de Python para escribir datos en BigQuery desde PubSub usando Apache Beam.
  * https://github.com/jpgiraldor/proyecto_practica/blob/8e4de9d208062d55c9619fd10df94ccb2b4fcbee/beam_ps_bq.py
 
 #### Enunciado Parte 2 ####
 Para la segunda parte de este ejercicio, vamos a utilizar un dataset público de GCP acerca de los taxis de Chicago.
 
 `TIP` No hacer un query `Select *` ya que sale demasiado caro, si desea ver el diccionario de datos puede entrar a este link:
 https://www.kaggle.com/paultimothymooney/how-to-query-the-chicago-taxi-dataset/data
 
 Entre los pasos preliminares es agregar la tabla a BigQuery. Para haccer esto, debe de ingresar a este link en el mismo navegador donde tiene GCP abierto y buscar el dataset.
 * https://console.cloud.google.com/marketplace/browse?filter=solution-type:dataset&_ga=2.29011196.1907405029.1639873486-138552656.1629748128
 * ![image](https://user-images.githubusercontent.com/35697253/146681315-5095de3c-ffd2-44c6-991b-9370e503f1be.png)
 * ![image](https://user-images.githubusercontent.com/35697253/146681337-895e00f6-0bac-4ab3-a413-5fb3b1450b28.png)

 Se desea averiguar la siguiente informacion:
 * Cuantos drop-offs tiene cada `dropoff_location` y organizarlos de más a menos.
 * Máxima, mínima y tarifa promedio de los viajes de 10 minutos o más.
 * Los 10 `dropoff_location` con mayor tip.
 * Cuales son los `pickup_location` y `dropoff_location` de los 15 viajes más costosos.

 * Respuestas *
 * ![image](https://user-images.githubusercontent.com/35697253/146689021-8f4cd8ef-9277-41dd-a80d-518e6c75acfc.png)
 * ![image](https://user-images.githubusercontent.com/35697253/146688638-6c2c25cc-715c-4469-aaa0-ffc0eb14ef3f.png)
 * ![image](https://user-images.githubusercontent.com/35697253/146688652-2f5bdd08-aa54-4e64-a798-3691f25e535a.png)
 * ![image](https://user-images.githubusercontent.com/35697253/146689333-4b63d7c8-7ef7-4bd9-98e4-6828996612fe.png)



 

 

     
