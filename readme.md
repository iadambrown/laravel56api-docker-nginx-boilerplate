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
docker-compose up -d --build
docker ps -a
docker exec -it <container_id> bash
php /srv/app/artisan migrate
```
(production)
```bash
docker-compose --file=docker-compose.prod.yml up -d build
```

##### Xdebug:
```bash
Prefs > Languages & Frameworks > PHP > Debug
Port: 9001
Can leave "force break with script outside project"

Run/Debug Dropdown > Edit Configurations
+ PHP Web Page
Server: Localhost
Start URL: /
[...] (server)

Host: localhost
Port: 8080
√ Path mappings
/Code/docker-lamp        /srv/app
Start Listening
```
