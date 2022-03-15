# Instalasi Laravel di Ubuntu

#### Install PHP

```
sudo apt install zip unzip software-properties-common 
sudo add-apt-repository ppa:ondrej/php 
sudo apt install -y php7.4 php7.4-gd php7.4-mbstring php7.4-xml php-zip 
```

#### Install Apache2

```
sudo apt install apache2 libapache2-mod-php7.4 
```

#### Install MySQL

```
sudo apt install mysql-server php7.4-mysql 
```

#### Install Composer

```
curl -sS https://getcomposer.org/installer | php 
sudo mv composer.phar /usr/local/bin/composer 
sudo chmod +x /usr/local/bin/composer 
```

#### Install with Clone Laravel

```
cd /var/www 
git clone https://github.com/laravel/laravel.git 
cd /var/www/laravel 
sudo composer install 
chown -R www-data.www-data /var/www/laravel 
chmod -R 755 /var/www/laravel 
chmod -R 777 /var/www/laravel/storage 
mv .env.example .env 
php artisan key:generate 
```

```
sudo nano .env 
```

```
APP_NAME=Laravel
APP_ENV=local
APP_KEY=base64:HFdS7c9rhDp+AeHu7kc2OLBPuxHqq2BQ/1gfFWEpoAk=
APP_DEBUG=true
APP_URL=http://localhost
...
```

#### Create Database

```
CREATE DATABASE laravel;
CREATE USER 'laravel'@'localhost' IDENTIFIED BY 'secret';
GRANT ALL ON laravel.* to 'laravel'@'localhost';
FLUSH PRIVILEGES;
quit
```

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=secret
```

```
vim /etc/apache2/sites-enabled/000-default.conf 
```

```
<VirtualHost *:80>

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/laravel/public

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/laravel>
                AllowOverride All
        </Directory>

</VirtualHost>
```

```
sudo systemctl restart apache2 
```

#### Remove Package

```
composer remove vendor/package 
```

####
