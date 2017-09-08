# docker-crib
A personal aide mémoire containing useful docker commands largely for specific local developement use-cases. 

## MariaDB / MySQL
Create a MariaDB / MySQL database which supports accented indexes.
```
% docker exec <db_container_id> mysql -u <mysql_user> -p<password> -e 'DROP DATABASE IF EXISTS <dbname>;CREATE DATABASE <dbname> DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_bin; GRANT ALL ON <dbname>.* TO <dbuser>;
```
## PHP
Run a remote PHP script so that it connects to the IntelliJ / PHPStorm debugger.
```
% docker exec -e PHP_IDE_CONFIG="serverName=<phpstorm_server_configuration_name>" -u <webserver_user> <php_container_id> php /path/to/the/script.php
```
