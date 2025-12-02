# Démarrage du Raspberry Pi

Il y a 2 solutions pour démarrer le RPI :
- Basculer le switch sur le coté du Raspberry,
![[switch.jpg|250]]
- Brancher un câble USB-C sur le Raspberry.
![[usbc.jpg|300]]

!!! info
	Le temps de démarrage du Raspberry est d'environ 20 secondes.

---
# Éteindre le Raspberry

- Inverser l'interrupteur sur le côté,
![[switch.jpg|250]]
- Débrancher le câble USB-C.

---
# Connexion à distance au Raspberry Pi en utilisant RealVNC Viewer

1. Créer un partage de connexion Wi-Fi sans chiffre ni caractères spéciaux pour le mot de passe (ex : PassWord)

2. Connecter le Raspberry Pi au Wi-Fi en cliquant sur le SSID avec le stylet tactile en haut à droite de l'écran
![[Wifi.png|250]]
3. Cliquer sur l'icône de clavier et entrer le mot de passe avec le stylet
![[Screenshot 2024-05-27 161521.png]]

4. Consulter l'adresse IP du Raspberry dans les paramètres

5. Dans RealVNC, entrer l'adresse IP du Raspberry 
![[Screenshot 2024-05-27 161810.png]]

6. Dans la Pop-up, cliquer sur "Continue" et entrer les informations de connexion :
	- Identifiant : pi
	- Mot de passe : Billon

!!! note 
	Félicitations, vous êtes connecté !

!!! warning
	Il est également possible de se connecter simplement en SSH, seulement, j'ai préféré utiliser une vue graphique pour tester l'attaque de phishing en local

---
# Lancement des applications de pentesting

!!! info
	Toutes les applications se lancent depuis le terminal

# Applications testées

## ZPhisher
```
cd zphisher
sudo ./zphisher.sh
```
![[Screenshot 2024-05-27 163752.png|400]]

Choisir un template de connexion

Choisir 2 pour la redirection de ports avec Cloudflared et répondre "**N**" aux deux questions
![[Screenshot 2024-05-27 163933.png|400]]

Une fois que les URLs apparaissent, copier la 1ère, lancer un nouveau terminal et PhishMailer.

---
## PhishMailer
```
cd PhishMailer
sudo python3 PaishMailer.py
```
![[Screenshot 2024-05-27 163305.png|400]]

Choisir le template de phishing et remplir les informations demandées (prénom de la victime, email, date…)

Coller l'URL de ZPhisher

Entrer l'adresse mail de la victime, le nom du fichier et c'est fini

Transférer le fichier html *(/home.pi/PhishMailer/"nomfichier.html)* sur la machine hôte et l'insérer dans un mail puis l'envoyer.
Maintenant, il ne reste plus qu'à attendre que la victime clique sur le lien et rentre ses identifiants.

---
## DHCPig

```
sudo dhcpig -c -v3 -l -a -i -o wlan0
```
Ensuite, attendre.

!!! info
	Si on souhaite arrêter l'attaque : CTRL + C

---
## Lynis

```
sudo ./lynis audit system -Q
```
Ensuite, attendre que le scan se termine.

---
# Attaques non testées

## Metasploit Console

```
msfconsole
```
[Basics | Metasploit Documentation](https://docs.metasploit.com/docs/using-metasploit/basics/)

---
## Aircrack-NG

```
aircrack-ng [options] <capture file(s)>
```
[newbie_guide [Aircrack-ng]](https://www.aircrack-ng.org/doku.php?id=newbie_guide)

---
## Airgeddon

```
cd airgeddon
sudo bash airgeddon.sh
```
[How to perform Evil Twin WiFi Attack | GoLinuxCloud](https://www.golinuxcloud.com/evil-twin-wifi-attack/)

---
## Wifiphisher

```
ifconfig wlan0 down  
iwconfig wlan0 mode monitor  
ifconfig wlan0 up
wifiphisher -i wlan0 -e "SSID" -p oauth-login
```
Attendre que quelqu'un se connecte au réseau.

[Tutorial: Wifiphisher Attack | Medium](https://medium.com/@mikewittenauer/tutorial-wifiphisher-attack-create-fake-wifi-networks-for-hacking-8ac242fb9a37)

---
# Tester le Packet Tracer

!!! info
	Le but du Packet Tracer est d'illustrer une attaque Evil Twin sur un réseau

!!! note
	Ouvrir le fichier **ESP_PT_neuf.pkt**
![[Cégep/ESP_PT_neuf.pkt]]
## Se connecter au Wi-Fi

Cliquer sur **Laptop0**

Dans **Desktop** > **Wireless PC** > **Profiles** > **New**

Entrer un nom (ex : Wireless1)

Choisir le réseau sans-fil à rejoindre dans la liste :
- Wireless-Network = Vrai Wi-Fi
- Wireless-Netw0rk = Fake Wi-Fi
![[Pasted image 20240527171948.png]]

Cliquer sur **Connect**

Si vous avez choisi le **faux Wi-Fi** : Vous êtes connecté

!!! warning "À savoir"
	Avec un Evil Twin réel, vous devez entrer un mot de passe, n'importe lequel sera valable, il n'est juste pas possible de faire un réseau avec une authentification mais un mot de passe vide dans Packet Tracer

Si vous avez choisi le **vrai Wi-Fi** :
![[Pasted image 20240527172049.png]]

Entrer le mot de passe : **P4ssW0rd**

Vous êtes connecté