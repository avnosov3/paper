# paper

# Запуск проекта

Проект можно запустить через docker или скачать репозиторий с github

Чтобы было удобнее посмотреть способ формирования подписок нужно сделть следующие шаги последовательно

1. Дёрнуть [ручку](http://127.0.0.1:8000/api/v1/auto/fill-source), которая заполнит источники в БД
2. Дёрнут [ручку](http://127.0.0.1:8000/api/v1/auto/fill-user), которая заполнит пользователей в БД
3. Дёрнут [ручку](http://127.0.0.1:8000/api/v1/auto/fill-subscriptions), которая заполнит подписки пользователей в БД
4. Дёрнут [ручку](http://127.0.0.1:8000/api/v1/auto/fill-posts), которая заполнит посты в БД

# Через Docker

Клонировать репозиторий и перейти в него в командной строке

```
git clone git@github.com:avnosov3/paper.git
cd paper/
```

Создать .env и заполнить

```
DB_ENGINE=postgresql+asyncpg
POSTGRES_DB=chief
POSTGRES_USER=<Указать имя пользователя>
POSTGRES_PASSWORD=<Указать пароль пользователя>
DB_HOST=db
DB_PORT=5432
```

Запустить docker compose

```
docker compose up -d
```

Провести миграции

```
docker compose exec paper poetry run alembic upgrade head
```

# Через GitHub


Клонировать репозиторий и перейти в него в командной строке

```
git clone git@github.com:avnosov3/paper.git
cd paper/
```

Установить зависимости

```
poetry install
```

Создать .env и заполнить

```
DB_ENGINE=postgresql+asyncpg
POSTGRES_DB=chief
POSTGRES_USER=<Указать имя пользователя>
POSTGRES_PASSWORD=<Указать пароль пользователя>
DB_HOST=localhost
DB_PORT=5432
```

Провести миграции
```
poetry run alembic upgrade head
```

Запустить проект

```
poetry run uvicorn app.main:app
```

# Документация

После запуска документация будет доступна в виде
* [swagger](http://127.0.0.1:8000/docs/)
* [redoc](http://127.0.0.1:8000/redoc/)

* [Админка postgres](http://127.0.0.1:8080/) доступ будет только при работе с docker