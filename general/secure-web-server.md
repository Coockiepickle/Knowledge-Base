
## 1. Pré-requis

- Serveur Debian (Raspberry Pi ou autre) avec accès sudo.  
- SSH déjà fonctionnel.  
- Ports souhaités ouverts :  
  - SSH sur 12222  
  - HTTP sur 80  
  - HTTPS sur 443  
  
***

## 2. Installation des outils

### Mettre à jour le système

`sudo apt update && sudo apt upgrade -y`

### Installer Fail2Ban et UFW

`sudo apt install fail2ban ufw`

Fail2Ban protège contre le brute-force en bannissant les IP malveillantes via le pare-feu.  
  
***

## 3. Sécurisation SSH (clés + config)

### 3.1. Génération de la clé SSH côté client

Sur votre poste (Linux/macOS/WSL) :

`ssh-keygen -t ed25519 -C "commentaire_ou_mail"`

Acceptez le chemin par défaut et définissez une passphrase.

Copiez la clé publique vers le serveur :

`ssh-copy-id -i ~/.ssh/id_ed25519.pub user@serveur`

Vérifiez que la connexion par clé fonctionne :

`ssh -i ~/.ssh/id_ed25519 user@serveur`

### 3.2. Durcir `/etc/ssh/sshd_config`

Éditez la configuration SSH :

`sudo nano /etc/ssh/sshd_config`

Points essentiels :

- Interdire le login root :  
    - `PermitRootLogin no`  
- Interdire l’authentification par mot de passe :  
    - `PasswordAuthentication no`  
    - `PermitEmptyPasswords no`  
- Optionnel : limiter les comptes autorisés :  
    - `AllowUsers user`

Avant de recharger :

`sudo sshd -t    # vérifier la syntaxe`

Rechargez le service (en laissant une session SSH ouverte au cas où) :

`sudo systemctl reload ssh`

### 3.3. Changer le port SSH par défaut

Dans le même fichier :

- Remplacez `Port 22` par `Port 12222` (ou autre port non standard) 

Rechargez :

`sudo systemctl reload ssh`

Testez la connexion :

`ssh -p 12222 user@serveur`

Avec la clé créée précédemment :

`ssh -i ~/.ssh/id_ed25519 -p 12222 user@serveur`  
  
***

## 4. Configuration UFW (pare-feu)

### 4.1. Politique par défaut

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Tout ce qui arrive est bloqué par défaut, tout ce qui sort est autorisé.

### 4.2. Autoriser uniquement SSH 12222, HTTP 80, HTTPS 443

```bash
sudo ufw allow 12222/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```


### 4.3. Activer UFW et vérifier

```bash
sudo ufw enable
sudo ufw status verbose
```

Vous devez voir : incoming deny, outgoing allow, et les trois ports autorisés.

Il est également possible de supprimer les règles IPv6 pour n'autoriser que les connexions IPv4 :

`sudo ufw status numbered # lister les règles avec un ID`

Exemple de résultat :

```bash
1   12222/tcp   ALLOW   Anywhere
2   80/tcp      ALLOW   Anywhere
3   443/tcp     ALLOW   Anywhere
4   80/tcpv6    ALLOW   Anywhere (v6)
5   443/tcpv6   ALLOW   Anywhere (v6)
6   12222/tcpv6 ALLOW   Anywhere (v6)
```

puis

```bash
sudo ufw delete 4
sudo ufw delete 5
sudo ufw delete 6
```  
  
***

## 5. Configuration Fail2Ban

### 5.1. Fichier `jail.local`

Créer un fichier de configuration local :

`sudo nano /etc/fail2ban/jail.local`

Exemple minimal avec intégration UFW :

```ini
[DEFAULT]
bantime  = 15m
findtime = 15m
maxretry = 3
ignoreip = 127.0.0.1/8 ::1
backend  = systemd
banaction = ufw

[sshd]
enabled  = true
port     = 12222
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 3
```

- `bantime` : durée de ban.  
- `findtime` : fenêtre de temps pour compter les échecs.  
- `maxretry` : nombre d’essais avant ban.

### 5.2. Protection basique Nginx

Ajouter :

```ini
[nginx-http-auth]
enabled  = true
filter   = nginx-http-auth
logpath  = /var/log/nginx/error.log
maxretry = 3
```


### 5.3. Redémarrer et vérifier Fail2Ban

```bash
sudo systemctl enable --now fail2ban
sudo systemctl restart fail2ban
```

État général :

`sudo fail2ban-client status`

État du jail SSH :

`sudo fail2ban-client status sshd`

État du jail Nginx :

`sudo fail2ban-client status nginx-http-auth`

Vous verrez les IP bannies, le nombre de tentatives, etc.  

***

## 6. Résumé opérationnel

- SSH :
    - Accès uniquement par clé.
    - Port déplacé en 12222.
    - Root interdit.
- UFW :
    - Tout entrant bloqué, IPv6 bloqué, sauf :
      - 12222/tcp (SSH)
      - 80/tcp (HTTP)
      - 443/tcp (HTTPS)
- Fail2Ban :
    - Surveille les logs SSH et Nginx.
    - Bannis automatiquement les IP qui bruteforcent.

