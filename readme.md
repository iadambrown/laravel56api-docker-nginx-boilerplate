### Setup:

##### MariaDB:
```dotenv
DB_CONNECTION=mysql
DB_HOST=mariadb
DB_PORT=3306
DB_USERNAME=root
# Other values based on docker-compose.yml "services > mariadb > environment" settings
```

##### Docker:
```bash
docker-compose up -d --build && docker-compose exec app php artisan migrate --seed
docker exec -it app bash
```
(production)
```bash
docker-compose --file=docker-compose.prod.yml up -d build
```

##### Xdebug:
```
Prefs > Languages & Frameworks > PHP > Debug
Port: 9001
Can leave "force break with script outside project"

Run/Debug Dropdown > Edit Configurations
+ PHP Web Page
Server: Localhost
Start URL: /
[...] (add server)

Host: localhost
Port: 8080
√ Path mappings
/Code/path-to-project        /srv/app
Start Listening
```
