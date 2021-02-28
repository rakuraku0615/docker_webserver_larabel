# docker_webserver_larabel

docker compose set for laravel web serber

 - app : php:7.4.15-fpm-buster
 - apache :  nginx:1.18-alpine
 - db : mysql:8.0

## set up

clone repo
```
git clone https://github.com/rakuraku0615/docker_webserver_laravel.git
```

move to repo dir
```
cd docker_webserver_laravel
```

build
```
docker_webserver_laravel
```

set laravel
```
docker-compose exec app bash
```

```
## in app
# composer
composer install

# set env file
cp .env.example .env

# generate laravel app key
php artisan key:generate

# migrate
php artisan migrate
```

access to localhost

http://localhost:8080/
