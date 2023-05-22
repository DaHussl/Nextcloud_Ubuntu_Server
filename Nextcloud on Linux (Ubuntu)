# updating 
apt update && apt upgrade -y

# Installing apache
apt install apache2

# Install PHP 8.1 
apt install software-properties-common
add-apt-repository ppa:ondrej/php
apt update

# Install PHP 8.1 & Moduls
apt install php8.1 libapache2-mod-php8.1 php8.1-zip php-dompdf php8.1-xml php8.1-mbstring php8.1-gd php8.1-curl php8.1-imagick libmagickcore-6.q16-6-extra php8.1-intl php8.1-bcmath php8.1-gmp php8.1-cli php8.1-mysql php8.1-zip php8.1-gd  php8.1-mbstring php8.1-curl php8.1-xml php-pear unzip nano php8.1-apcu redis-server ufw php8.1-redis

# adjust PHP.ini file
nano /etc/php/8.1/apache2/php.ini
memory_limit = 1024M
upload_max_filesize = 16G
post_max_size = 16G
date.timezone = Europe/Berlin
output_buffering = Off

# Install Databse Server
apt install mariadb-server

# Maria DB Server Konfiguration
mysql_secure_installation

# open SQL dialoge
mysql

# create database calles nextcloud
CREATE DATABASE nextcloud; 

# create database user with password
CREATE USER 'nextclouduser'@'localhost' IDENTIFIED BY 'password_here';

#grant accesss to databse
GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextclouduser'@'localhost';

#save changes and exit
FLUSH PRIVILEGES;
EXIT;

# Download lastest nextcloud version
cd /tmp && wget https://download.nextcloud.com/server/releases/latest.zip
unzip latest.zip
mv nextcloud /var/www/

#create new conf
nano /etc/apache2/sites-available/nextcloud.conf
<VirtualHost *:80>
     ServerAdmin master@domain.com
     DocumentRoot /var/www/nextcloud/
     ServerName cloud.domain.org
     <Directory /var/www/nextcloud/>
        Options +FollowSymlinks
        AllowOverride All
        Require all granted
          <IfModule mod_dav.c>
            Dav off
          </IfModule>
        SetEnv HOME /var/www/nextcloud
        SetEnv HTTP_HOME /var/www/nextcloud
     </Directory>
     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
 
# Enable the NextCloud and Rewrite Module
a2ensite nextcloud.conf
a2enmod rewrite
a2enmod headers
a2enmod env
a2enmod dir
a2enmod mime

# restart apache
service apache2 restart

# prepare data folder
mkdir /home/data/
chown -R www-data:www-data /home/data/
chown -R www-data:www-data /var/www/nextcloud/
chmod -R 755 /var/www/nextcloud/