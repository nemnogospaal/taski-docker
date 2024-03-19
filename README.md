# Taski-docker

### Описание проекта:
Проект представляет собой трекер задач.



### Как запустить проект:
`git clone git@github.com:nemnogospaal/taski-docker.git`  клонировать репозиторий

**Docker**\
    Перед началом нужно установить и запустить Docker.\
    `docker-compose up`  запустить Docker Compose\
    Открыть новый терминал\
    `docker compose exec backend python manage.py collectstatic`  cобрать статику Django
    `docker compose exec backend cp -r /app/collected_static/. /backend_static/static/`  копируем статику на volume\
    `docker compose exec backend python manage.py migrate`  выполнить миграции\
    `docker compose exec backend python manage.py createsuperuser` создать суперпользователя\

После запуска будут доступны следующие адреса:

    - главная  http://localhost:8000/

    - админка  http://localhost:8000/admin/

Дополнительные команды для работы:
    `docker compose up --build`  пересборка контейнеров\
    `docker-compose stop`  остановить Docker Compose\
    `docker-compose down`  остановить Docker Compose и удалить все контейнеры

При запуске использовались следующие версии пакетов:
- Nodejs -> v15.9.0
- npm -> 7.5.3
- Python -> 3.9.10
- pip -> 24.0

Запуск **backend**\

    `python -m venv venv`  создать виртуальное окружение\
    `source venv/Scripts/activate`  активировать виртуальное окружение\
    `python -m pip install --upgrade pip`  обновить окружение\
    `cd backend`  Перейдите в директорию backend\
    `pip install -r requirements.txt`  установить зависимости из файла requirements.txt\
    `python manage.py migrate`  выполнить миграции\
    `python manage.py createsuperuser`  создать суперпользователя\
    `python manage.py runserver`  запустить проект

Запуск **frontend**\

`cd frontend`  перейти в директорию frontend\
`npm i`  установить зависимости\
`npm run start`  запуск приложения

После запуска будут доступны следующие адреса:
- главная -> http://localhost:3000/
- админка -> http://127.0.0.1:8000/admin/

### Cписок используемых технологий:

- Django
- React
- djangorestframework
- Docker

### Как заполнить файл .env:
В проекте есть файл .env.example заполните свой по аналогии.

`POSTGRES_USER` - пользователь БД\
`POSTGRES_PASSWORD` - пароль БД\
`POSTGRES_DB` - название БД\
`DB_HOST` - имя контейнера, где запущен сервер БД\
`DB_PORT` - порт, по которому Django будет обращаться к БД\
