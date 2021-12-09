Dockerfile для бэкенда в каталоге lib_catalog  
Dockerfile для БД в каталоге db_postgres  
Используем python:3.9.7-alpine, обновляем зависимости.  
Команды для сборки:  
docker build -t dockertask02 .  
docker build -t database .  
docker run --name database --net bridge -h database --ip 172.17.0.2 -p 5432:5432 -e POSTGRES_PASSWORD=django -e POSTGRES_USER=django -e POSTGRES_DATABASE=django -d database  
docker run --net bridge -h backend -p 8000:8000 --name backend dockertask02  
  
  
Урлы Апишки  
./src/AuthorApi.js:const API_URL = 'http://localhost:8000/api/v1/lib/author/';  
./src/BBKApi.js:const API_URL = 'http://localhost:8000/api/v1/lib/bbk/';  
./src/BookApi.js:const API_URL = 'http://localhost:8000/api/v1/lib/book/';  
./src/CitiesApi.js:const API_URL = 'http://localhost:8000/api/v1/lib/issue_city/';  
./src/CityApi.js:const API_URL = 'http://localhost:8000/api/v1/lib/issue_city/';  
./src/KeyWordAPI.js:const API_URL = 'http://localhost:8000/api/v1/lib/key_word/';  
./src/PubApi.js:const API_URL = 'http://localhost:8000/api/v1/lib/publishing_house/';  
  
Проверим связь в докер контейнере доставить пинг  
apt-get update && apt-get install -y iputils-ping  
  
Инфа из исходников  
DATABASES = {  
    "default": {  
        "ENGINE": "django.db.backends.postgresql",  
        "NAME": "django",  
        "USER": "django",  
        "PASSWORD": "django",  
        "HOST": "database",  
        "PORT": "5432",  
        "CONN_MAX_AGE": None  
    }  