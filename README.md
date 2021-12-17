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
    * Como preferencia propia, recomiendo instalar PyCharm como IDE de Python.
    * Instalar los siguientes modulos de python con pip
      * `pip install google-cloud`
      * `pip install google-cloud-storage`
      * `pip install google-cloud-pubsub`
      * `pip install google-cloud-bigquery`
      * `pip install google-cloud-bigquery-storage`
      * `pip install google-apitools`
      * `pip install apache-beam `
     
