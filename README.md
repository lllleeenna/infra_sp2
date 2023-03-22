## Проект: запуск docker-compose для API YaMDb
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

### Заполнение базы данных контентом:
```
docker-compose exec web python manage.py shell  
```
``` 
from django.contrib.contenttypes.models import ContentType
ContentType.objects.all().delete()
quit()
```
```
docker-compose exec web python manage.py loaddata fixtures.json
```
