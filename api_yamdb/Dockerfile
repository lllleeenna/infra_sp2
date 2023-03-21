# Создать образ на основе базового слоя python
FROM python:3.7-slim

#Сделать директорию рабочей
WORKDIR /app

# Скопировать с локального компьютера в /app
COPY . .

# Выполнить установку зависимостей внутри контейнера
RUN pip3 install -r requirements.txt --no-cache-dir

#Выполнить запуск сервера разработки при старте контейнера
CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000"]
