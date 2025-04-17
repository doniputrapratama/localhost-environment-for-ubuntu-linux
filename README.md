# This is only for ubuntu linux desktop environment not intended for ubuntu linux server or other linux servers
# Before installing this new localhost environment, it is recommended to delete the old localhost environment and backup your projects and database before continuing with the installation.

# Follow the terminal commands below for installation, don't make any mistakes or skip any steps. You must follow each step.

# BASIC PREPARATION
# System Update
  <pre lang="markdown"> sudo apt update && sudo apt upgrade -y </pre>
# INSTALL APACHE
  <pre lang="markdown"> sudo apt install apache2 -y </pre>
# Enable and Check Apache Status
  <pre lang="markdown"> sudo systemctl enable apache2 </pre> <br>  <pre lang="markdown"> sudo systemctl status apache2 </pre>
# setting access rights
  <pre lang="markdown"> sudo chown -R www-data:www-data /var/www/html </pre> <br> <pre lang="markdown"> sudo chmod -R 755 /var/www/html </pre>
# INSTALL MYSQL
  <pre lang="markdown"> sudo apt install mysql-server -y </pre>
# Run and Secure MySQL
  <pre lang="markdown"> sudo systemctl enable mysql </pre> <br> <pre lang="markdown"> sudo mysql_secure_installation </pre>
# Mysql server configuration
# Login to MySQL as root
  <pre lang="markdown"> sudo mysql -u root -p </pre>
# Once logged in, change the password with the command
# Change YourNewPassword! with the password you want, minimum 8 characters with upper and lower case letters and have the character '@' and a number, for example Admin@123
 <pre lang="markdown"> ALTER USER 'root'@'localhost' IDENTIFIED BY 'YourNewPassword!'; </pre> <br> <pre lang="markdown"> FLUSH PRIVILEGES; </pre>
# Changing Password Policy
  <pre lang="markdown"> SHOW VARIABLES LIKE 'validate_password%'; </pre> <br> <pre lang="markdown"> SET GLOBAL validate_password.policy = 0; </pre> <br> <pre lang="markdown"> EXIT; </pre>
# INSTALL PHP
# Add PHP PPA and Install PHP
  <pre lang="markdown"> sudo add-apt-repository ppa:ondrej/php </pre> <br> <pre lang="markdown"> sudo apt update </pre> <br> <pre lang="markdown"> sudo apt install php php-cli php-common php-mbstring php-xml php-bcmath php-curl php-mysql php-zip php-gd php-soap php-intl libapache2-mod-php unzip curl -y </pre>
# APACHE CONFIGURATION FOR PHP
# Enable Apache Module & Restart
  <pre lang="markdown"> sudo a2enmod php </pre> <br> <pre lang="markdown"> sudo systemctl restart apache2 </pre>
# INSTALL PHPMYADMIN
# Go to the following link to download phpmyadmin in .zip format
  <pre lang="markdown"> https://www.phpmyadmin.net/ </pre> <br> <pre lang="markdown"> cd ~/Downloads </pre>
# change x.x.x according to the version downloaded for this phpMyAdmin-x.x.x-all-languages.zip
  <pre lang="markdown"> unzip phpMyAdmin-x.x.x-all-languages.zip </pre> <br> <pre lang="markdown"> sudo mv phpMyAdmin-x.x.x-all-languages /var/www/html/phpmyadmin </pre>
# or copy all the files in the phpMyAdmin-x.x.x-all-languages ​​folder that has been extracted to the /var/www/html/phpmyadmin folder. If there is no phpmyadmin folder, please create it first.
# Set Access Rights
  <pre lang="markdown"> sudo chown -R www-data:www-data /var/www/html/phpmyadmin </pre> <br> <pre lang="markdown"> sudo chmod -R 755 /var/www/html/phpmyadmin </pre>
# Create Configuration File open your terminal
  <pre lang="markdown"> cd /var/www/html/phpmyadmin </pre> <br> <pre lang="markdown"> cp config.sample.inc.php config.inc.php </pre>
# Edit config.inc.php open yor terminal
  <pre lang="markdown"> sudo nano config.inc.php </pre>
# Cari baris
  <pre lang="markdown"> $cfg['blowfish_secret'] = ''; </pre>
# Fill with a random string of at least 32 characters
  <pre lang="markdown"> $cfg['blowfish_secret'] = '1x!2y@3z#4a$5b%6c^7d&8e*9f(0g)h'; </pre>
# Then save (CTRL+O then ENTER, CTRL+X to exit).
# Open your browser and visit
  <pre lang="markdown"> http://localhost/phpmyadmin </pre>
# INSTALL NODE.JS & NPM
# install the stable version
  <pre lang="markdown"> sudo snap install node --classic </pre>
# INSTALL COMPOSER
# Open your Terminal
  <pre lang="markdown"> cd ~ </pre> <br> <pre lang="markdown"> php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" </pre> <br> <pre lang="markdown"> php composer-setup.php </pre> <br> <pre lang="markdown"> sudo mv composer.phar /usr/local/bin/composer </pre> <br> <pre lang="markdown"> composer --version </pre>
# And all is done please make your project happily








