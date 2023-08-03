# Respuestas

Indica tu nombre a continuación: 

Por cada etapa agrega una sección abajo y escribe las respuestas a las preguntas de cada etapa.

## ETAPA 1
¿Cuál es la diferencia entre los archivos con el verbo `Create` con los archivos con el verbo `Add`?
R.- Las migraciones con el verbo `Create` crean tablas, mientras que las migraciones con el verbo `Add` agregan columnas a tablas ya existentes.

¿Cómo se llama el servicio que se declara en el archivo `docker-compose.yml`?
R.- El servicio se llama `flyway`.

¿Cuál es el comando que se ejecuta en el servicio declarado?
R.- El comando que se ejecuta es `flyway -locations=filesystem:/flyway/sql -connectRetries=60 migrate`.

## ETAPA 2

¿Qué pasa si cambias el nombre del servicio de `postgres` a `db`? ¿Qué otros cambios tendrías que hacer?
R.- Tendría que cambiarse a `db` el nombre del servicio en el archivo `docker-compose.yml`, el valor en la seccion `depends_on` del servicio `flyway`, y en el archivo `.env` el valor de la variable `POSTGRES_SERVER`


## ETAPA 3

Revisa el archivo `movies-api/Dockerfile`. ¿Qué te llama la atención?
R.- Que se utiliza una imagen de Go para construir la imagen del servicio, apoyandose en el archivo `go.mod` para instalar las dependencias.

¿Cómo se relacionan el archivo `docker-compose.yml` y el archivo `movies-api/Dockerfile`? 
R.- El archivo `docker-compose.yml` define el servicio `movies-api` que levanta un contenedor `movies_api_container` a partir de la imagen definida en el archivo `movies-api/Dockerfile`.

¿Qué crees que hace el atributo `context` debajo de `build` (está en la linea 6 del archivo `docker-compose.yml`)?
R.- El atributo `context` indica la ruta donde se encuentra el archivo `Dockerfile` que se usará para construir la imagen del servicio.

Intenta cambiar el puerto a 8080.
¿Qué pasa si en vez `movies-api` usas `localhost` para la variabla `BIND_IP`?
R.- No se puede acceder al servicio desde el navegador, ya que el servicio no está expuesto en el puerto 8000 de localhost, sino en el puerto 8000 del contenedor `movies_api_container`

## ETAPA 4

Compara los archivos `Dockerfile` de `movies-api` y `movies-front`. 
R.- El archivo `Dockerfile` de `movies-api` utiliza una imagen de Go para construir la imagen del servicio, mientras que el archivo `Dockerfile` de `movies-front` utiliza una imagen de Node para construir la imagen del servicio.

Compara el atributo `build` del servicio `movies-api` con el de `movies-front`. 
¿Cuál es la diferencia? 
R.- La diferencia es que en movies-api se indica un contexto que contiene el directorio con prefijo `./`, mientras que en movies-front se indica solo el nombre del directorio.
¿Qué pasa si los dejas iguales?
R.- Funciona igualmente, pues ambos archivos `Dockerfile` se encuentran en el directorio raíz de cada servicio.