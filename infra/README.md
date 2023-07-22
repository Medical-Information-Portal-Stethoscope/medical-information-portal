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


## Прод

### Self-signed certificate
```
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ./nginx.key -out ./nginx.crt
```