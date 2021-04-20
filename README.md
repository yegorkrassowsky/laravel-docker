# Laravel-docker boilerplate

## Setup:

1. Clone this repository
```console
git clone https://github.com/yegorkrassowsky/laravel-docker.git
```

2. Set permissions on the project directory so that it is owned by your non-root user
```console
sudo chown -R $(whoami) ./
```

3. Copy the .env.example file that Laravel includes by default and name the copy .env, which is the file Laravel expects to define its environment
```console
cp .env.example .env
```

4. Modify .env
```
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laraveluser
DB_PASSWORD=your_laravel_db_password
```

5. Edit mysql root password in docker-compose.yml file
```
MYSQL_ROOT_PASSWORD: your_laravel_db_password
```

6. Run docker-compose
```console
docker-compose up -d
```

7. Wait for composer installs all dependencies

```console
docker logs composer
```

8. The following command will generate a key and copy it to your .env file, ensuring that your user sessions and encrypted data remain secure
```console
docker-compose exec app php artisan key:generate
```

9. To cache these settings into a file, which will boost your application’s load speed, run:
```console
docker-compose exec app php artisan config:cache
```

10. As a final step, visit http://your_server_ip in the browser. You will see the home page for your Laravel application
