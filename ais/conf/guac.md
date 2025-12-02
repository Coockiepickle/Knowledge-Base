```
sudo apt-get update
sudo apt-get install build-essential libcairo2-dev libjpeg62-turbo-dev libpng-dev libtool-bin uuid-dev libossp-uuid-dev libavcodec-dev libavformat-dev libavutil-dev libswscale-dev freerdp2-dev libpango1.0-dev libssh2-1-dev libtelnet-dev libvncserver-dev libwebsockets-dev libpulse-dev libssl-dev libvorbis-dev libwebp-dev -y
cd /tmp
wget https://downloads.apache.org/guacamole/1.5.5/source/guacamole-server-1.5.5.tar.gz
tar -xzf guacamole-server-1.5.5.tar.gz
cd guacamole-server-1.5.5/
sudo ./configure --with-init-dir=/etc/init.d
```
```
sudo make
sudo make install
sudo ldconfig
sudo systemctl daemon-reload
sudo systemctl start guacd
sudo systemctl enable guacd
sudo systemctl status guacd
```
```
sudo mkdir -p /etc/guacamole/{extensions,lib}
sudo apt-get install tomcat9 tomcat9-admin tomcat9-common tomcat9-user
```
```
cd /tmp
wget https://downloads.apache.org/guacamole/1.5.5/binary/guacamole-1.5.5.war
sudo mv guacamole-1.5.5.war /var/lib/tomcat9/webapps/guacamole.war
sudo systemctl restart tomcat9 guacd
sudo apt-get install mariadb-server
sudo mysql_secure_installation
mysql -u root -p
```
```
CREATE DATABASE guacadb;
CREATE USER 'guaca_user'@'localhost' IDENTIFIED BY 'Password';
GRANT SELECT,INSERT,UPDATE,DELETE ON guacadb.* TO 'guaca_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
```
cd /tmp
wget https://downloads.apache.org/guacamole/1.5.5/binary/guacamole-auth-jdbc-1.5.5.tar.gz
tar -xzf guacamole-auth-jdbc-1.5.5.tar.gz
sudo mv guacamole-auth-jdbc-1.5.5/mysql/guacamole-auth-jdbc-mysql-1.5.5.jar /etc/guacamole/extensions/
```
```
cd /tmp
wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-j-9.0.0.tar.gz
tar -xzf mysql-connector-j-9.0.0.tar.gz
sudo cp mysql-connector-j-9.0.0/mysql-connector-j-9.0.0.jar /etc/guacamole/lib/
cd guacamole-auth-jdbc-1.5.5/mysql/schema/
cat *.sql | mysql -u root -p guacadb
```
```
sudo nano /etc/guacamole/guacamole.properties
```

# MySQL
```
mysql-hostname: 127.0.0.1
mysql-port: 3306
mysql-database: guacadb
mysql-username: guaca_user
mysql-password: Password
```
```
sudo nano /etc/guacamole/guacd.conf
```
```
[server] 
bind_host = 0.0.0.0
bind_port = 4822
```
```
sudo systemctl restart tomcat9 guacd mariadb
```
http://adresse_ip:8080/guacamole/
