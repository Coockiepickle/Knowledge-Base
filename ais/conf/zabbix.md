`wget https://repo.zabbix.com/zabbix/7.2/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.2+debian12_all.deb`

`dpkg -i zabbix-release_latest_7.2+debian12_all.deb`

`apt update`

[[Install MySQL]]

`apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent`

`mysql -uroot -p`
`mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;`
`mysql> create user zabbix@localhost identified by 'password';`
`mysql> grant all privileges on zabbix.* to zabbix@localhost;`
`mysql> set global log_bin_trust_function_creators = 1;`
`mysql> quit;`

`zcat /usr/share/zabbix/sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix`

`mysql -uroot -p`
`mysql> set global log_bin_trust_function_creators = 0;`
`mysql> quit; `

`sudo nano /etc/zabbix/zabbix_server.conf`

```
DBHost=localhost
DBName=zabbix
DBUser=zabbix
DBPassword=password
```

`sudo systemctl restart zabbix-server zabbix-agent apache2`

`sudo systemctl enable zabbix-server zabbix-agent apache2`

### Configurer l'interface web

http://10.23.0.32/zabbix

Choisir la langue > Prochaine étape > Vérifier les prérequis > Prochaine étape

Configurer la connexion à la bdd :

![[Screenshot 2025-06-02 at 09-08-17 Installation.png]]

Choisir un nom pour le serveur > choisir la bonne timezone > Prochaine étape

Se connecter avec les identifiants suivants : 
username : Admin
password : zabbix

### Installer et activer l'agent sur l'hôte

`sudo apt install zabbix-agent`

`sudo systemctl start zabbix-agent`

#### Configurer l'agent

`sudo nano /etc/zabbix/zabbix_agentd.conf`

```
Server=10.23.0.32
ServerActive=10.23.0.32
```

`sudo systemctl restart zabbix-agent`

### Ajouter un hôte

Dans la colonne de gauche de l'interface Zabbix, Choisir "Collecte de données" > "Hôtes"

![[Screenshot 2025-06-02 at 10-08-23 zabbix-mfdr Configuration des hôtes.png]]

1. Entrer les informations de l'hôte

2. Dans "Interfaces", choisir "Agent" et entrer l'IP de l'hôte

3. Dans l'onglet "IPMI", entrer le nom d'utilisateur et le mot de passe de l'hôte 

4. Dans l'onglet "Inventaire", choisir "Automatique"

![[Screenshot 2025-06-02 at 10-08-42 zabbix-mfdr Configuration des hôtes.png]]

Enfin, cliquer sur "Ajouter"

### Ajouter un trigger

Dans "Collecte de données" > Modèles

Choisir un modèle > "Déclencheurs" > "Créer un déclencheur"

Entrer les informations du déclencheur

![[Screenshot 2025-06-02 at 10-56-49 zabbix-mfdr Configuration des déclencheurs.png]]

Cliquer sur "Ajouter"

Dans la colonne de gauche, dans "Alertes" > "Actions" > "Actions de déclencheur"

Donner un nom à l'alerte, puis cliquer sur "Ajouter" dans "Conditions"

Choisir le déclencheur créé précédemment puis cliquer sur "Ajouter"

Lier le modèle à l'hôte, redémarrer la machine et vérifier l'apparition de l'alerte sur le tableau de bord

