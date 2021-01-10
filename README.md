# PHP
## Install PHP7.3-FPM
https://github.com/zupaazhai/install-php7-3-fpm

# MySQL
## Install MySQL
```
apt update
apt install mysql-server
mysql_secure_installation
```
## Reset root password for MySQL for Version 5.7.x
```
service mysql stop
mkdir /var/run/mysqld
chown mysql: /var/run/mysqld
mysqld_safe --skip-grant-tables --skip-networking &
mysql -uroot mysql
UPDATE mysql.user SET authentication_string=CONCAT('*', UPPER(SHA1(UNHEX(SHA1('NEWPASSWORD'))))), plugin='mysql_native_password' WHERE User='root' AND Host='localhost';
mysqladmin -S /var/run/mysqld/mysqld.sock shutdown
service mysql start
```
