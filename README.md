# Docker

## Dockerfile
`Dockerfile` - это файл в котором можно описать образ или настройки для образа.

### Задание
необходимо создать проект и запустить в нем проект с сервером, что бы результат отображался в браузере

### Выполнение

Для начала необходимо создать файл PHP и указать данные которые будут отображаться в браузере.

Создаем файл index.php и добавляем данные для отображения в браузере
![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_16.png?raw=true)
Далее создаем файл Dockerfile и указываем там следующие данные:
![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_15.png?raw=true)

~~~
FROM - образ для копирования
WORKDIR - рабочая папка 
COPY - папка для копирования образа
EXPOSE - порт
~~~

Теперь это необходимо собрать и посмотреть как всё работает.
Для этого проверяем имеющиеся контейнеры командой:
~~~
docker image
~~~

и запускаем сам файл Dockerfile
~~~
docker run -p 8001:80 -d my-php-app
~~~

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_18.png?raw=true)

Теперь мы можем перейти в браузере по адресу `localhost:8001` и увидедь данные из файла `index.php`

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_17.png?raw=true)



## Docker-compose

`Docker-compose` - это файл в котором возможно описать множество образов проекта и настройки к этим образам.

### Задание

- Подключить PHPMyAdmin
- Подключить Mysql
- Подключить PHP

### Выполнение

#### PHPmyAdmin

Сначала необходимо создать файл `Docker-compose.yml` и добавить в него настройки PHPmyAdmin. Сами настройки взяли с сайта dockerhub.com

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_5.png?raw=true)

Теперь неоходимо изменить строку `MYSQL_ROOT_PASSWORD` и добавить пароль для входа.

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_7.png?raw=true)

Для запуска контейнера необходимо его собрать командой:
~~~
docker-compose build
~~~

И запустить:
~~~
docker-compose up
~~~

Теперь мы можем зайти по адресу `localhost:8080`

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_8.png?raw=true)

После авторизации мы попадаем на главную страницу

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_9.png?raw=true)

#### MySQL

Для подключения MySQL необходимо в файле `docker-compose.yml` редактировать строку `image` и добавить строку `command`

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_10.png?raw=true)

После создаем образ и запускаем его:
~~~
docker-compose build
docker-compose up
~~~

И заходим по адресу `localhost:8080`

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_11.png?raw=true)

#### PHP

Для подключения PHP необходимо в файле `docker-compose.yml` добавить сервис `php` и задать настройки

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_12.png?raw=true)

Для наглядности, меняем данные в файле `index.php`

После создаем образ и запускаем его:
~~~
docker-compose build
docker-compose up
~~~

Заходим по адресу `localhost:8081` и `localhost:8080`

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_13.png?raw=true)

![ufw](https://github.com/PopChop88/Docker/blob/main/рис/Screenshot_11.png?raw=true)
