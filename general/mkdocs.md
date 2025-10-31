# Installation MKDocs

### Installation Python + pip, environnement Python, installation et création MKDocs

```bash
sudo apt install python3 pip
python3 -m venv mkdocs-env
source mkdocs-env/bin/activate
pip install mkdocs
mkdocs --version
mkdocs new docs
cd docs
```

#### Pour Serveur local

```bash
mkdocs serve
```

[Test MKDocs](http://127.0.0.1:8000)


### Installation theme

```bash
pip install mkdocs-material
```

### Exemple de configuration MKDocs

```bash
sudo nano mkdocs.yml
```

```bash
site_name: Documentation Technique
theme:
  name: material
  language: fr
nav:
  - Accueil: index.md
  - Réseau:
    - VLAN: réseau/vlan.md
  - Sécurité:
    - Firewall: sécurité/firewall.md
markdown_extensions:
  - admonition
  - codehilite
  - toc:
    permalink: true
plugins:
  - search
```

#### Pour Serveur web

```bash
mkdocs build
```

### Installation + Configuration Apache

```bash
sudo apt install apache2

sudo mkdir -p /var/www/html/mkdocs
sudo cp -r site/* /var/www/html/mkdocs/
```

### Configuration reverse-proxy

```bash
sudo nano /etc/apache2/sites-available/reverse-proxy.conf
```

```bash
<VirtualHost *:443>
    ServerName docs.dreynaud.ipv64.net
    ProxyPass / http://127.0.0.1:8081/
    ProxyPassReverse / http://127.0.0.1:8081/

    DocumentRoot /var/www/html/mkdocs
    <Directory /var/www/html/mkdocs>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
    </Directory>

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/docs.crt
    SSLCertificateKeyFile /etc/ssl/private/docs.key

    RequestHeader set X-Forwarded-Proto "https"
    RequestHeader set X-Forwarded-Port "443"

    ErrorLog ${APACHE_LOG_DIR}/mkdocs_error.log
    CustomLog ${APACHE_LOG_DIR}/mkdocs_access.log combined
</VirtualHost>

<VirtualHost *:443>
    ServerName portfolio.dreynaud.ipv64.net
    ProxyPass / http://127.0.0.1:8082/
    ProxyPassReverse / http://127.0.0.1:8082/

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/portfolio.crt
    SSLCertificateKeyFile /etc/ssl/private/portfolio.key

    RequestHeader set X-Forwarded-Proto "https"
    RequestHeader set X-Forwarded-Port "443"

    ErrorLog ${APACHE_LOG_DIR}/portfolio_error.log
    CustomLog ${APACHE_LOG_DIR}/portfolio_access.log combined
</VirtualHost>
```

### Activation plugins Apache

```bash
sudo a2enmod ssl proxy proxy_http headers
```

### Certificat Let's Encrypt

```bash
sudo certbot --apache -d docs.dreynaud.ipv64.net
```

### Activation site

```bash
sudo a2ensite reverse-proxy.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
```

[Test MKDocs HTTPS](https://127.0.0.1:8081) | [Test MKDocs Internet](https://docs.dreynaud.ipv64.net)

