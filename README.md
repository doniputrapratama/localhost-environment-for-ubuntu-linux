# This is only for ubuntu linux desktop environment not intended for ubuntu linux server or other linux servers
# Before installing this new localhost environment, it is recommended to delete the old localhost environment and backup your projects and database before continuing with the installation.

# Follow the terminal commands below for installation, don't make any mistakes or skip any steps. You must follow each step.

# BASIC PREPARATION
# System Update
  sudo apt update && sudo apt upgrade -y
# INSTALL APACHE
  sudo apt install apache2 -y
# Enable and Check Apache Status
  sudo systemctl enable apache2```
  sudo systemctl status apache2
# setting access rights
  sudo chown -R www-data:www-data /var/www/html
  sudo chmod -R 755 /var/www/html
# INSTALL MYSQL
  sudo apt install mysql-server -y
# Run and Secure MySQL
  sudo systemctl enable mysql
  sudo mysql_secure_installation
# Mysql server configuration
# Login to MySQL as root
  sudo mysql -u root -p
# Once logged in, change the password with the command
# Change YourNewPassword! with the password you want, minimum 8 characters with upper and lower case letters and have the character '@' and a number, for example Admin@123
  ALTER USER 'root'@'localhost' IDENTIFIED BY 'YourNewPassword!';
  FLUSH PRIVILEGES;
# Changing Password Policy
  SHOW VARIABLES LIKE 'validate_password%';
  SET GLOBAL validate_password.policy = 0;
  EXIT;
# INSTALL PHP
# Add PHP PPA and Install PHP
  sudo add-apt-repository ppa:ondrej/php
  sudo apt update
  sudo apt install php php-cli php-common php-mbstring php-xml php-bcmath php-curl php-mysql php-zip php-gd php-soap php-intl libapache2-mod-php unzip curl -y
# APACHE CONFIGURATION FOR PHP
# Enable Apache Module & Restart
  sudo a2enmod php
  sudo systemctl restart apache2
# INSTALL PHPMYADMIN
# Go to the following link to download phpmyadmin in .zip format
  https://www.phpmyadmin.net/
  cd ~/Downloads
# change x.x.x according to the version downloaded for this phpMyAdmin-x.x.x-all-languages.zip
  unzip phpMyAdmin-x.x.x-all-languages.zip
  sudo mv phpMyAdmin-x.x.x-all-languages /var/www/html/phpmyadmin
# or copy all the files in the phpMyAdmin-x.x.x-all-languages ​​folder that has been extracted to the /var/www/html/phpmyadmin folder. If there is no phpmyadmin folder, please create it first.
# Set Access Rights
  sudo chown -R www-data:www-data /var/www/html/phpmyadmin
  sudo chmod -R 755 /var/www/html/phpmyadmin
# Create Configuration File open your terminal
  cd /var/www/html/phpmyadmin
  cp config.sample.inc.php config.inc.php
# Edit config.inc.php open yor terminal
  sudo nano config.inc.php
# Cari baris
  $cfg['blowfish_secret'] = '';
# Fill with a random string of at least 32 characters
  $cfg['blowfish_secret'] = '1x!2y@3z#4a$5b%6c^7d&8e*9f(0g)h';
# Then save (CTRL+O then ENTER, CTRL+X to exit).
# Open your browser and visit
  http://localhost/phpmyadmin
# INSTALL NODE.JS & NPM
# Open your browser and go to the following link
  https://snapcraft.io/node
# install the stable version
  sudo snap install node --classic
# INSTALL COMPOSER
# Open your Terminal
  cd ~
  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
  php composer-setup.php
  sudo mv composer.phar /usr/local/bin/composer
  composer --version
# And all is done please make your project happily








