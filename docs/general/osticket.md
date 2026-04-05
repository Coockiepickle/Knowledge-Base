## Installation osTicket

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y
sudo systemctl enable --now apache2
sudo systemctl start mariadb
sudo apt install php8.4 php8.4-common php8.4-gd php8.4-imap php8.4-ctype php8.4-opcache php8.4-intl \
php8.4-bcmath php8.4-fpm php8.4-apcu php8.4-cli php8.4-mbstring php8.4-phar php8.4-curl php8.4-mysql \
php8.4-json php8.4-xml php-pear php8.4-cgi php8.4-iconv libapache2-mod-php8.4 php8.4-ldap mariadb-server mariadb-client
sudo systemctl enable --now mariadb
```
  
---

## Configuration de MariaDB

Démarrer l'installation intéractive mysql :

`sudo mysql_secure_installation`


`sudo mysql -u root`

```bash
CREATE DATABASE osticket;
CREATE USER 'osticketuser'@'localhost' IDENTIFIED BY 'P@ssw0rd1';
GRANT ALL PRIVILEGES ON osticket.* TO 'osticketuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
  
---

## Téléchargement et configuration d'osTicket

```bash
wget https://github.com/osTicket/osTicket/releases/download/v1.17.4/osTicket-v1.17.4.zip
sudo apt install unzip
unzip osTicket-v1.17.4.zip -d /var/www/
sudo chown -R www-data:www-data /var/www/osTicket/
sudo nano /etc/apache2/sites-available/osticket.conf
```
  
---

## Configuration d'Apache

```bash
<VirtualHost *:80>
    ServerAdmin admin@mail.com
    DocumentRoot /var/www/osTicket/upload
    ServerName example.com
    <Directory /var/www/osTicket/upload/>
        Options FollowSymlinks
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/osticket_error.log
    CustomLog ${APACHE_LOG_DIR}/osticket_access.log combined
</VirtualHost>
```
  
---

## Activation des modules et redémarrage d'Apache

```bash
sudo a2enmod php8.4
sudo a2ensite osticket.conf
sudo systemctl reload apache2
sudo systemctl restart apache2
```
  
---

## Accès à l'interface web

`http://localhost`

Paramétrer les informations de base (admin email, password, etc.)  
  
---

## Finalisation de l'installation

```bash
sudo chmod 0644 /var/www/osTicket/upload/include/ost-config.php
sudo rm -rf /var/www/osTicket/upload/setup/
```

