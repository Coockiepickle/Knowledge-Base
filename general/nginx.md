
## 1. Installation de Nginx

### 1.1 Installation

`sudo apt update && sudo apt install nginx -y`

Vérifier le service :

`systemctl status nginx`

Activer au démarrage si besoin :

`sudo systemctl enable nginx`

### 1.2 Organisation des vhosts

Nginx utilise :

- `/etc/nginx/sites-available/` pour les fichiers de config “déclarés”  
- `/etc/nginx/sites-enabled/` pour les sites “activés” via symlink  
- `nginx -t` pour valider la config, puis `systemctl reload nginx`  
  
***

## 2. Certificats avec Certbot (Let’s Encrypt)

### 2.1 Pré‑requis

- DNS du domaine → IP publique de ton serveur  
- Un vhost HTTP simple avec `server_name` correct.

Exemple HTTP pour `example.com` :

```nginx
server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/example.com/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

### 2.2 Installation de Certbot

`sudo apt install certbot python3-certbot-nginx -y`


### 2.3 Obtention du certificat + config auto Nginx

`sudo certbot --nginx -d example.com -d www.example.com`

Certbot :

- obtient le certificat  
- ajoute un bloc `listen 443 ssl;` avec `ssl_certificate` et `ssl_certificate_key`  
- peut configurer la redirection HTTP → HTTPS si tu choisis cette option.

Test du renouvellement :

`sudo certbot renew --dry-run`  
  
***

## 3. Certificats self‑signed

### 3.1 Génération du certificat

`sudo mkdir -p /etc/nginx/ssl`

puis,

`sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/ssl/example.key -out /etc/nginx/ssl/example.crt`

Enfin, remplir les informations suivantes (optionnel mais recommandé) :

- Country Name : ex. FR  
- State or Province : ex. France  
- Locality Name : ex. Limoges  
- Organization Name : ex. DReynaud  
- Organizational Unit : ex. Development  
- Common Name (FQDN) : ex. example.com  
- Email Address : ex. dev@example.com


### 3.2 Vhost HTTPS avec self‑signed

```nginx
server {
    listen 443 ssl;
    listen [::]:443 ssl;
    http2 on;

    server_name dev.local;

    root /var/www/dev/html;
    index index.html;

    ssl_certificate     /etc/nginx/ssl/example.crt;
    ssl_certificate_key /etc/nginx/ssl/example.key;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Redirection HTTP → HTTPS :

```nginx
server {
    listen 80;
    listen [::]:80;
    server_name dev.local;
    return 301 https://$host$request_uri;
}
```

Les navigateurs afficheront un avertissement (Autorité de Certification non reconnue), normal pour de l'auto-signé.  

***

## 4. Activer le HTTPS (générique)

Pour n’importe quel site :

1. Avoir un bloc HTTP :

   ```nginx
   server {
       listen 80;
       server_name example.com;
       return 301 https://$host$request_uri;
   }
   ```

2. Avoir un bloc HTTPS :

   ```nginx
   server {
       listen 443 ssl;
       listen [::]:443 ssl;
       http2 on;

       server_name example.com;

       root /var/www/example.com/html;
       index index.html;

       ssl_certificate     /chemin/vers/fullchain.pem;
       ssl_certificate_key /chemin/vers/privkey.pem;

       location / {
           try_files $uri $uri/ =404;
       }
   }
   ```

3. Vérifier et recharger :

   ```bash
   sudo nginx -t
   sudo systemctl reload nginx
   ```  
  
***

## 5. Héberger plusieurs sites sur le même serveur

### 5.1 Arborescence

Exemple pour 3 sites :

```bash
sudo mkdir -p /var/www/site1/html
sudo mkdir -p /var/www/site2/html
sudo mkdir -p /var/www/site3/html

sudo chown -R $USER:$USER /var/www/site{1,2,3}/html
```

Mettre un `index.html` différent dans chaque dossier.

### 5.2 Vhosts HTTP + HTTPS par domaine

Il est possible d'avoir un seul fichier de configuration pour tous les sites, ou un fichier par site.

```nginx
# Site 1
server {
    listen 80;
    server_name site1.example.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    listen [::]:443 ssl;
    http2 on;

    server_name site1.example.com;

    root /var/www/site1/html;
    index index.html;

    ssl_certificate     /etc/letsencrypt/live/site1.example.com/cert.crt;
    ssl_certificate_key /etc/letsencrypt/live/site1.example.com/cert.key;

    location / {
        try_files $uri $uri/ =404;
    }
}

# Site 2
server {
    listen 80;
    server_name site2.example.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    listen [::]:443 ssl;
    http2 on;

    server_name site2.example.com;

    root /var/www/site2/html;
    index index.html;

    ssl_certificate     /etc/letsencrypt/live/site2.example.com/cert.crt;
    ssl_certificate_key /etc/letsencrypt/live/site2.example.com/cert.key;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

- Un `server_name` précis par domaine.  
- Un bloc HTTP (80) + un bloc HTTPS (443) pour chaque site.  
- Symlinks dans `sites-enabled` si tu sépares les fichiers.

