                            # Frontend + Backend

### Этап 1: Установка Laravel + Nginx + Mysql


1. Manage .env
 
   ```cp .env.example .env```

   **DOCKER_USER** - system username<br>
   **DOCKER_UID** - system user uid (1000)<br>
   **DOCKER_BACKEND_PORT** - external backend port <br>
   **DOCKER_NGINX_LISTEN_PORT** - internal backend port<br>
   **DOCKER_SERVER_NAME** - app url (site.loc)<br>
   **DOCKER_FRONT_PORT** - external frontend port<br>
   **DOCKER_MYSQL_PORT** - mysql external port<br>

   ###### .env for mysql
   **DB_HOST**=<br>
   **DB_PORT**=<br>
   **DB_DATABASE**=<br>
   **DB_USERNAME**=<br>
   **DB_PASSWORD**=<br><br>

2.  Установка Laravel

    ```
    docker-compose build
    docker-compose up [-d]
    sudo chown [your-system-user]:www-data backend
    docker exec -it l11-app bash
    composer create-project --prefer-dist laravel/laravel ./
    ```
    На этапе создания проекта Laravel важно убедиться, что директория backend доступна для записи от имени пользователя контейнера.<br>
    После установки указываем переменные в .env Пользователя и пароль для БД должны совпадать с указанными для Docker

3.  Установка Vue

    ```
    docker-compose build
    docker-compose up [-d]
    ```

    3.1 подключаемся к контейнеру
    ```
    docker exec -it l11-node bash
    ```

    3.2 создание проекта [my-project] и копирование в рабочую директорию
    ```
    vue create project
    cp -r project/* html/ 
    rm -rf project/
    chown -R node:node html/
    ```
    Проверить работу vue:
    ```cd html ``` ``` yarn serve ``` В браузере открыть localhost с указанием порта объявленного в DOCKER_FRONT_PORT
    