# docker-crib
A personal aide mémoire containing useful docker commands largely for specific local developement use-cases. 

## Docker images
Remove an image (usually before rebuilding having updated its Dockerfile).
```
% docker rmi <image_name>
```
Build an image using a Dockerfile assuming it exists in the `cwd`.
```
% docker build -t <name_for_the_image> .
```
Without caching.
```
% docker build --no-cache -t <name_for_the_image> .
```

## Working with containers
Mostly `docker exec` snippets here.
### MariaDB / MySQL
Create a MariaDB / MySQL database which supports accented indexes.
```
% docker exec <db_container_id> mysql -u <mysql_user> -p<password> -e 'DROP DATABASE IF EXISTS <dbname>;CREATE DATABASE <dbname> DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_bin; GRANT ALL ON <dbname>.* TO <dbuser>;
```
### PHP
Run a remote PHP script so that it connects to the IntelliJ / PHPStorm debugger.

```
# Passing -e PHP_IDE_CONFIG="serverName=<phpstorm_server_configuration_name>"
# sets the necessary environment variable:
% docker exec -e PHP_IDE_CONFIG="serverName=<phpstorm_server_configuration_name>" -u <webserver_user> <php_container_id> php /path/to/the/script.php
```
### Moodle
This assumes a Debian based container running Apache hence `www-data` user.
```
docker exec -u www-data <container_id> php /path/to/admin/cli/install_database.php \
--adminuser=admin \
--adminpass=<admin_password> \
--adminemail=<admin_email> \
--fullname=<site_name> \
--shortname=<site_short_name> \
--agree-license
```
