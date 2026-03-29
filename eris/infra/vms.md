
#### Infos :

| pfSense-DR | debian | WS-DR          | W10     |
| ---------- | ------ | -------------- | ------- |
| admin      | std    | Administrateur | Admin   |
| 443        | 10222  | 13389          |         |

#### Nom de domaine : 
DR.ERIS

#### DB : 

| Nom DB | glpi | ncdb   |
| ------ | ---- | ------ |
| User   | glpi | ncuser |

#### MDP : 
Drowssap1

##### Nextcloud Admin MDP : 
Z44HzRphs4

#### IP :

|     | pfSense          | Debian               | WS-2022       | W10                   |
| --- | ---------------- | -------------------- | ------------- | --------------------- |
| LAN | 192.168.1.1/24   | 192.168.1.101 (DHCP) | 192.168.1.100 | DHCP VPN (10.0.0.2-3) |
| GW  | 172.16.1.213     | 192.168.1.1          | 192.168.1.1   | 192.168.1.1           |
| WAN | 172.16.13.249/16 |                      |               | DHCP 3iL              |

TOTP Debian Scratch Codes : 
38083251
99200099
14271817
70891083
57961368

GLPI VHost : 
```
<VirtualHost *:80>
    ServerName 192.168.1.101
    ServerAlias 192.168.1.101
    DocumentRoot /var/www/glpi/public

    <Directory /var/www/glpi/public>
        Options FollowSymLinks
        AllowOverride All
        Require all granted
        RewriteEngine On

        RewriteCond %{HTTP:Authorization} ^(.+)$
        RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^(.*)$ index.php [QSA,L]
    </Directory>

    # Sécurité basique
    <Directory /var/www/glpi>
        Options -Indexes
        AllowOverride None
    </Directory>

    # En-têtes utiles
    Header always set X-Content-Type-Options "nosniff"
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set X-XSS-Protection "1; mode=block"

    ErrorLog ${APACHE_LOG_DIR}/glpi_error.log
    CustomLog ${APACHE_LOG_DIR}/glpi_access.log combined
</VirtualHost>
```

#### Nextcloud VHost :
```
Alias /nextcloud "/var/www/nextcloud/"

<Directory /var/www/nextcloud/>
  Require all granted
  AllowOverride All
  Options FollowSymLinks MultiViews

  <IfModule mod_dav.c>
    Dav off
  </IfModule>
</Directory>
```
