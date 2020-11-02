## Docker's command helpers
- Запуск контейнеров `docker-compose up -d --build`
- Остановка контейнеров `docker-compose down`
- Просмотр логов `docker-compose logs --tail 25`

## Laravel's command helpers
- Установить Laravel `composer create-project --prefer-dist laravel/laravel <NameProj>`
- Установить Laravel другой версии `composer create-project --prefer-dist laravel/laravel:^7.0 <NameProj>`

## Access phpMyAdmin to DB
- docker exec -it db bash
- mysql -u root -p
- CREATE USER 'root'@'%' IDENTIFIED BY 'root';
- GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
- FLUSH PRIVILEGES;