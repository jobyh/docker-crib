# docker-crib
A personal aide mémoire containing useful docker commands largely for very specific local developement use-cases. 

## MariaDB / MySQL
Create a MariaDB / MySQL database which supports accented indexes.
```
docker exec <db_container_id> mysql -u <mysql_user> -p<password> -e 'DROP DATABASE IF EXISTS <dbname>;CREATE DATABASE <dbname> DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_bin; GRANT ALL ON <dbname>.* TO <dbuser>;
```
