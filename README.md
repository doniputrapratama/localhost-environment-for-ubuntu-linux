<h1>Localhost Environment for Ubuntu linux Dekstop</h1>

<p>This is only for ubuntu linux desktop environment not intended for ubuntu linux server or other linux servers</p>
<p>Before installing this new localhost environment, it is recommended to delete the old localhost environment and backup your projects and database before continuing with the installation.</p>

<p>Follow the terminal commands below for installation, don't make any mistakes or skip any steps. You must follow each step.</p>

<h2>BASIC PREPARATION</h2>
<h3>System Update</h3>
  <pre lang="markdown"> sudo apt update && sudo apt upgrade -y </pre>
<h3>INSTALL APACHE</h3>
  <pre lang="markdown"> sudo apt install apache2 -y </pre>
<h3>Enable and Check Apache Status</h3>
  <pre lang="markdown"> sudo systemctl enable apache2 </pre> <br>  <pre lang="markdown"> sudo systemctl status apache2 </pre>
<h3>setting access rights</h3>
  <pre lang="markdown"> sudo chown -R www-data:www-data /var/www/html </pre> <br> <pre lang="markdown"> sudo chmod -R 755 /var/www/html </pre>
<h3>INSTALL MYSQL</h3>
  <pre lang="markdown"> sudo apt install mysql-server -y </pre>
<h3>Run and Secure MySQL</h3>
  <pre lang="markdown"> sudo systemctl enable mysql </pre> <br> <pre lang="markdown"> sudo mysql_secure_installation </pre>
<h3>Mysql server configuration</h3>
<h3>Login to MySQL as root</h3>
  <pre lang="markdown"> sudo mysql -u root -p </pre>
<h3>Once logged in, change the password with the command</h3>
<p>Change 'YourNewPassword!' with the password you want, minimum 8 characters with upper and lower case letters and have the character '@' and a number, for example 'Admin@123'</p>
 <pre lang="markdown"> ALTER USER 'root'@'localhost' IDENTIFIED BY 'YourNewPassword!'; </pre> <br> <pre lang="markdown"> FLUSH PRIVILEGES; </pre>
<h3>Changing Password Policy</h3>
  <pre lang="markdown"> SHOW VARIABLES LIKE 'validate_password%'; </pre> <br> <pre lang="markdown"> SET GLOBAL validate_password.policy = 0; </pre> <br> <pre lang="markdown"> EXIT; </pre>
<h3>INSTALL PHP</h3>
<h3>Add PHP PPA and Install PHP</h3>
  <pre lang="markdown"> sudo add-apt-repository ppa:ondrej/php </pre> <br> <pre lang="markdown"> sudo apt update </pre> <br> <pre lang="markdown"> sudo apt install php php-cli php-common php-mbstring php-xml php-bcmath php-curl php-mysql php-zip php-gd php-soap php-intl libapache2-mod-php unzip curl -y </pre>
<h3>APACHE CONFIGURATION FOR PHP</h3>
<h3>Enable Apache Module & Restart</h3>
  <pre lang="markdown"> sudo a2enmod php </pre> <br> <pre lang="markdown"> sudo systemctl restart apache2 </pre>
<h3>INSTALL PHPMYADMIN</h3>
<p>Go to the following link to download phpmyadmin in .zip format</p>
  <pre lang="markdown"> https://www.phpmyadmin.net/ </pre> <br> <pre lang="markdown"> cd ~/Downloads </pre>
<p>change x.x.x according to the version downloaded for this phpMyAdmin-x.x.x-all-languages.zip</p>
  <pre lang="markdown"> unzip phpMyAdmin-x.x.x-all-languages.zip </pre> <br> <pre lang="markdown"> sudo mv phpMyAdmin-x.x.x-all-languages /var/www/html/phpmyadmin </pre>
<p>or copy all the files in the phpMyAdmin-x.x.x-all-languages ​​folder that has been extracted to the /var/www/html/phpmyadmin folder. If there is no phpmyadmin folder, please create it first.</p>
<h3>Set Access Rights</h3>
  <pre lang="markdown"> sudo chown -R www-data:www-data /var/www/html/phpmyadmin </pre> <br> <pre lang="markdown"> sudo chmod -R 755 /var/www/html/phpmyadmin </pre>
<h3>Create Configuration File open your terminal</h3>
  <pre lang="markdown"> cd /var/www/html/phpmyadmin </pre> <br> <pre lang="markdown"> cp config.sample.inc.php config.inc.php </pre>
<h3>Edit config.inc.php open yor terminal</h3>
  <pre lang="markdown"> sudo nano config.inc.php </pre>
<h3>Search row</h3>
  <pre lang="markdown"> $cfg['blowfish_secret'] = ''; </pre>
<h3>Fill with a random string of at least 32 characters</h3>
  <pre lang="markdown"> $cfg['blowfish_secret'] = '1x!2y@3z#4a$5b%6c^7d&8e*9f(0g)h'; </pre>
<h3>Then save (CTRL+O then ENTER, CTRL+X to exit).</h3>
<h3>Open your browser and visit</h3>
  <pre lang="markdown"> http://localhost/phpmyadmin </pre>
<h3>INSTALL NODE.JS & NPM</h3>
<h3>install the stable version</h3>
  <pre lang="markdown"> sudo snap install node --classic </pre>
<h3>INSTALL COMPOSER</h3>
<h3>Open your Terminal</h3>
  <pre lang="markdown"> cd ~ </pre> <br> <pre lang="markdown"> php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" </pre> <br> <pre lang="markdown"> php composer-setup.php </pre> <br> <pre lang="markdown"> sudo mv composer.phar /usr/local/bin/composer </pre> <br> <pre lang="markdown"> composer --version </pre>
<h3>And all is done please make your project happily</h3>








