# Запуск нового проекта

1. Запуск Docker-compose

```bash
docker compose up -d
```

2. Установка Laravel

```bash
docker exec -ti php-fpm_8.2 bash -c "composer create-project --prefer-dist laravel/laravel ."
```

3. Настройка владельце для папки storage

```bash
docker exec -ti php-fpm_8.2 bash -c "chown -R www-data:www-data /var/www/html/storage"
```

4. Обновить .env

```env
DB_CONNECTION=pgsql
DB_HOST=postgres
DB_PORT=5432
DB_DATABASE=project
DB_USERNAME=project
DB_PASSWORD=project
```

5. Выполнение всех миграций

```bash
docker exec -ti php-fpm_8.2 bash -c "php artisan migrate"
```