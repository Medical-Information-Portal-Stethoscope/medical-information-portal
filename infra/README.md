## Запуск dev-сервера backend
- Переключиться на ветку develop (при необходимости)
```
git switch develop
```
- Получить изменения в ветке
```
git pull
```
- Обновить подмодули
```
git submodule update
```
- Перейти в директорию с docker-compose файлом
```
cd ./infra/dev
```
- Запустить docker-compose
```
docker compose -f docker-compose.backend.yml up -d --build
```

- Открыть страницу документации API [Swagger](http://localhost:8000/api/v1/swagger/) или [Redoc](http://localhost:8000/api/v1/redoc/)

## Доступ в админку
- Подключиться к контейнеру
```
docker compose -f docker-compose.backend.yml exec backend bash
```
- Создать суперпользователя
```
python manage.py createsuperuser
```
- Открыть панель администратора [localhost:8000/admin/](http://localhost:8000/admin/)


## Запуск локального сервера (для QA, без frontend)
- Клонировать репозиторий
```
git clone git@github.com:Medical-Information/medical-information-portal.git
```
- Перейти в директорию проекта
```
cd medical-information-portal
```
- Переключиться на ветку develop (при необходимости)
```
git switch develop
```
- Получить изменения в ветке
```
git pull
```
- Перейти в директорию с docker-compose файлом
```
cd ./infra/qa
```
- Скопировать файл .env.example в .env
```
cp .env.example .env
```
- Запустить docker-compose
```
docker compose -f docker-compose.backend.yml up -d
```
- Подключение к терминалу контейнера django_backend
```
docker compose -f docker-compose.backend.yml exec django_backend bash
```
или через терминал Docker Desktop
- Создать суперпользователя (при необходимости)
```
python manage.py createsuperuser
```
- Подключение к терминалу контейнера postgres
```
docker compose -f docker-compose.backend.yml exec postgres bash
```
или через терминал Docker Desktop
- Запустить psql
```
psql -U stethoscope_user -d stethoscope_db
```

### Self-signed certificate
```
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ./nginx.key -out ./nginx.crt
```

### M-1 problem
```
docker pull --platform linux/x86_64 gritsenkoserge/stethoscope-frontend:latest
docker pull --platform linux/x86_64 gritsenkoserge/stethoscope-backend:latest
```
