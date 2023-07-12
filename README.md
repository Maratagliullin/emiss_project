# Emiss
Автоматизация сбора и визуализация данных по показателям целей устойчивого развития (ЦУР) на национальном уровне!

**Задача**:    
Обеспечение автоматизированного сбора данных по показателям ЦУР из единой базы ЕМИСС и обеспечение их представление в сводном файле единого формата по причине того, что в настоящее время сбор таких данных осуществляется вручную из электронных таблиц,  отличающихся по своему структурному формату.  

**Результат:**     
Разработано web-приложение для автоматизации сбора данных показателей ЦУР в формате SDMX XML на языке Python с хранением данных в PostgreSQL и выгрузкой в единый файл формата (Excel) для визуализации в Yandex Datalens. Для удобства использования приложение обернуто в Docker.   

Пояснение к интерфейсу <a href="https://github.com/Maratagliullin/Emiss/blob/master/inteface.pdf" target="_blank">PDF.</a>

## Стек
Бекенд/Фронтенд - Django.  
Парсинг данных - Bs4, Selenoid.  
Очередь - Celery  
Docker  
База данных - Postgres

## Инструкция
### Предварительные действия:
Установка Docker - официальное руководство: https://docs.docker.com/get-docker/

Корректность установки необходимо проверить командой в терминале:

 ```docker --version```  

**Вывод:**  
 ```
Docker version 20.10.7, build f0df350  
 ```
Установка Docker-compose - официальное руководство:  https://docs.docker.com/compose/

Корректность установки необходимо проверить командой в терминале:

 ```docker-compose --version ```  

**Вывод:**  
 ```
 Docker Compose version v2.0.0-beta.6   
 ```
Скачивание образа браузера Chrome (команда):

```docker pull selenoid/chrome:91.0```   
```docker pull selenoid/firefox:89.0```   



### Запуск проекта:

Необходимо перейти в директорию проекта и запустить сборку командой:

```docker-compose build```  

Запуск проекта (команда):

```docker-compose up -d```  

### Перечень команд управления приложением (последовательное выполнение):  
**Ручной запуск парсинга ссылок на показатели:**  

```docker-compose exec WEB python3 manage.py parse_link```  

**Ручной запуск выгрузки SDMX:**  

```docker-compose exec WEB python3 manage.py parse_emis```  

**Ручной запуск обработки (парсинга) SDMX:** 

```docker-compose exec WEB python3 manage.py parse_data```  

##### Интерфейсы приложения:  
Django http://localhost:8000/admin    
Selenoid http://localhost:8081    
PgAdmin4 http://localhost:8082    
Учетные данные к сервисам расположены в .env файле в директории проекта (необходимо задать свои).   
