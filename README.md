# PHP
## Install PHP7.3-FPM
https://github.com/zupaazhai/install-php7-3-fpm
## Switch PHP 7.4 and 7.3
```
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update

sudo apt-get install php7.3
sudo apt-get install php7.3-cli php7.3-common php7.3-json php7.3-opcache php7.3-mysql php7.3-mbstring  php7.3-zip php7.3-fpm php7.3-intl php7.3-simplexml

sudo a2dismod php7.4
sudo a2enmod php7.3
sudo service apache2 restart

sudo update-alternatives --set php /usr/bin/php7.3
sudo update-alternatives --set phar /usr/bin/phar7.3
sudo update-alternatives --set phar.phar /usr/bin/phar.phar7.3
sudo update-alternatives --set phpize /usr/bin/phpize7.3
sudo update-alternatives --set php-config /usr/bin/php-config7.3
```

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
## Create new user for MySQL v.8
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'mypassword';
```
