## Проект «API для YaMDb»
Проект YaMDb собирает отзывы пользователей на произведения. 

### Технологии:
- Python 3.7
- Django 2.2.16
- djangorestframework 3.12.4
- PostgreSQL
- gunicorn
- nginx
- docker-compose

### env-файл:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
- DB_ENGINE - указываем с какрй БД работаем
- DB_NAME - имя базы данных
- POSTGRES_USER - логин для подключения к базе данных
- POSTGRES_PASSWORD - пароль для подключения к БД (установите свой)
- DB_HOST - название сервиса (контейнера)
- DB_PORT - порт для подключения к БД

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:lllleeenna/infra_sp2.git
```

```
cd infra
```

Запустите docker-compose:

```
docker-compose up
```

Выполнить миграции:

```
docker-compose exec web python manage.py migrate
```

Создайте суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```

Соберите статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

Остановка и удаление контейнеров:
```
docker-compose down -v
```

### Заполнение базы данных контентом с использованием manage.py
В папке /static/data/ находятся csv файлы с тестовыми данными для проекта YaMDb.

Для заполнения пустой БД введите команду:
```
python manage.py create_reviews
```

Для заполнения одной таблицы, используйте аргумент -t(--table)
Команда:
```
python manage.py create_reviews --table category
```
заполнить тестовыми данными таблицу category.

Если ваша БД содержит тестовые данные и вы действительно хотите их перезаписать
используйте аргумент --overwrite:
```
python manage.py create_reviews --overwrite
```

Для перезаписи данных одной таблицы используйтет команду:
```
python manage.py create_reviews --overwrite --table name_table
```
### Авторы:
1. Лещикова Татьяна (https://github.com/LeschikovaTatyana)
2. Дивногорская Ольга (https://github.com/OlyaDiv)
3. Смурова Елена (https://github.com/lllleeenna)
