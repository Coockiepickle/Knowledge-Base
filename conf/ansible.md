# Test Ansible

## Installation Ansible

```
sudo apt install ansible
```

## Fichier d'inventaire

```
sudo nano /etc/ansible/hosts
```

```
[serv_web]
docs.dreynaud.ipv64.net
portfolio.dreynaud.ipv64.net
web.dreynaud.ipv64.net

[firewalls]
pfsense.dreynaud.ipv64.net
```

### Commande de base pour groupe

```
ansible serv_web -m ping
```

### Exécuter commande shell

```
ansible all -m shell -a "uptime"
```

## Playbook

```
sudo nano /etc/ansible/install_apache.yml
```

```
- name: Installer Apache sur les serveurs web
  hosts: serv_web
  become: yes
  tasks:
    - name: Installer apache2
      apt:
        name: apache2
        state: present
```

### Exécuter Playbook

```
ansible-playbook install_apache.yml
```

### Playbook LAMP

```
- name: Installer LAMP sur Ubuntu
  hosts: web.dreynaud.ipv64.net
  become: yes
  tasks:
    - name: Installer Apache, MySQL, PHP
      apt:
        name:
          - apache2
          - mysql-server
          - php
          - libapache2-mod-php
        state: present
        update_cache: yes

    - name: Démarrer Apache
      service:
        name: apache2
        state: started
        enabled: yes
```

### Playbook Audit Lynis


```
- name: Audit de sécurité avec Lynis
  hosts: all
  become: yes
  tasks:
    - name: Installer Lynis
      apt:
        name: lynis
        state: present
    - name: Lancer un audit
      command: lynis audit system
      register: audit_output

    - name: Afficher le résultat
      debug:
        var: audit_output.stdout
``
```





