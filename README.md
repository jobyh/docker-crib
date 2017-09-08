# docker-crib
Docker crib sheet

```bash
# Create a MariaDB / MySQL database for Moodle / Totara which supports accented indexes.
docker exec <db_container_id> mysql -u <mysql_user> -p<password> -e 'DROP DATABASE IF EXISTS <dbname>;CREATE DATABASE <dbname> DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_bin; GRANT ALL ON <dbname>.* TO <dbuser>;
```
