# Proyecto NextJournal

Analisis y visualizaciones de la base de datos de genero y carreras universitarias en Argentina.

## Usar el repositorio

1. Clonar o descargar repositorio
2. `pip install -e .`

### ETL 
El ETL se encarga de procesar los datos en el la carpeta `data/input`, realizar el mapping entra las carreras y los grupos en las que queramos agruparlas, realizar la geolocalizacion de las universidades. Los resultados de la transformacion se guardan en la carpeta output y se utilizan para las visualizaciones.

El archivo `data/carreras.csv` contiene un listado de todas las carreras que se analizan e incluye, para cada una, su grupo (que se usa para agrupar grandes grupos de carreras) y su 'nombre normalizado' (que usamos para unificar nombres de carreras). Los grupos son, por ejemplo 'Juridicas, Económicas, Sociales, Naturales' y los nombres de carrera son, por ejemplo, 'Abogacia, Cs.Computacion, Medicina, Filosfia'. Todas las agrupaciones las realizamos de acuerdo a lo que queríamos analizar. El proceso fue automático(mediante macros y filtros directamente en la hoja de cálculos) y manual por lo que puede haber errores. Las carreras que quisimos dejar fuera del análisis las catalogamos como 'Otros', tanto en los grupos como en nombre normalizado. Esto se puede cambiar si se quisiera.

Para agregar un nuevo año al análisis, no solamente hay que agregarlo a carreras.csv sino tambien agregar los títulos que aparezcan en `data/validacion/titulos_nuevos.csv` y realizar el mapeo. 

Para procesamiento de los datos, de las maneras mencionadas

* Correr el proyecto `jupyter notebook`
* Abrir etl-next-journal.ipynb
* Realizar las modificaciones en los datos (o en el código) y correr el ETL (Cell --> Run All)


### Visualizaciones

El código que genera las visualizaciones utiliza los datos de la carpeta `data/output` generados por el ETL. Estos datos son autogenerados, por lo que recomendamos no modificarlos manualmente, sino usar el ETL para hacer cambios.

Para ver, usar y/o modificar las visualizaciones:

* Correr el proyecto `jupyter notebook`
* Abrir visualizaciones-next-journal.ipynb
* Correr el ETL (Cell --> Run All)

### Visualizaciones en HTML

Para generar una vista estática de las visualizaciones en HTML sin abrir el notebook:

* `make report`
