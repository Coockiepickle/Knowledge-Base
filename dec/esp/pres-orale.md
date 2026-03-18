
## Présentation Orale PP2 Damien Reynaud

---

## Sommaire

- Le but de mon ESP
- Pourquoi ?
- Les critères de succès
- Ce que j'ai réalisé
- Le réseau cible et sa version 2.0
- Les attaques que j'ai choisi
- Ce qu'il me reste à faire
- Les problèmes et leurs solutions
- Les limites du projet
- Ce que j'ai appris
- Sources d'information

---

## Le but de mon ESP

---

Le projet consiste à élaborer un **Système de Pentesting Portatif** (S.P.P) avec un Raspberry Pi.

![[Cégep/Images/RPI.jpg|500]]

---

## Pourquoi ?

- **Tester rapidement plusieurs attaques** sans avoir un ordinateur encombrant,

- Agréable d'avoir un **petit système polyvalent** de ce type,

- **Plus de possibilités** sur Linux que sur Windows,

- **Discrétion** 🤫🤫,

- **Plaisir d'utiliser Linux** et ma **passion pour les RPi**.

---

## Critères de succès

- Avoir un **Raspberry** de manière **Standalone**,
- Pouvoir **lancer plusieurs attaques** à partir du RPI,
- Pouvoir se connecter **à distance** à Raspbian.

---

## Ce que j'ai réalisé

- Installé Kali Linux sur un Raspberry Pi, mis en place un accès à distance,

- Fais de nombreuses recherches sur le fonctionnement d'attaques réseau,

- Testé plusieurs types d'attaques très répandues,

- Designé un réseau de test à attaquer sur [Draw.io](https://app.diagrams.net/),

- Designé une version améliorée du réseau sur Packet Tracer,

- Installé et configuré l'écran et la batterie sur le RPI,

- Réinstallé Raspbian et les applications de pentesting de Kali.

---

## Le réseau cible

![[Cégep/Images/Réseau Screenshot.png|600]]

---

## Version améliorée du réseau
![[Cégep/Images/Réseau PT.png|600]]

---

## Les attaques que j'ai choisi de réaliser 

---

### <font color="#ff0000">Audit de sécurité</font>

#### Avec Lynis

[Lynis - Security auditing tool - CISOfy](https://cisofy.com/lynis/)

`sudo ./lynis audit system -Q`

---

### 1ère attaque 

#### <font color="#ff0000">Attaque de phishing avec Zphisher et PhishMailer</font>

[PhishMailer (github.com)](https://github.com/BiZken/PhishMailer) / [Zphisher (github.com)](https://github.com/htr-tech/zphisher)

Zphisher : 

`sudo ./zphisher.sh`

PhishMailer : 

`sudo python3 Phishmailer.py`

---

### 2ème attaque

#### <font color="#ff0000">DHCP Exhaustion</font>

### Avec DHCPig

[dhcpig | Kali Linux Tools](https://www.kali.org/tools/dhcpig/) / [DHCPig GitHub](https://github.com/kamorin/DHCPig)

Juste **une** commande à taper :

`dhcpig -c -v3 -l -a -i -o wlan0`

---

### 3ème attaque (pas réalisable pour le moment)
#### <font color="#ff0000">Capture Wi-Fi + Crack de mot de passe Wi-Fi</font>

### Avec Aircrack-NG

[aircrack-ng | Kali Linux Tools](https://www.kali.org/tools/aircrack-ng/)


---

## Ce qu'il me reste à faire

- Acheter un dongle Wi-Fi pour le monitoring,

- Lancer l'attaque Evil Twin ([airgeddon | Kali Linux Tools](https://www.kali.org/tools/airgeddon/)),

- Lancer l'attaque de crack avec Aircrack-NG et intercepter le trafic réseau,

- Faire le réseau de manière physique,

- Faire fonctionner Kali Linux avec l'écran

---

## Les problèmes que j'ai rencontré

---

- Le modèle de valise que je voulais utiliser coûte **trop cher** (250 $CAD),

- Plusieurs applications de pentesting **ne fonctionnent que sur une architecture amd64** et pas sur une architecture **arm64** (RPI),

- Plusieurs applications nécessitent de mettre la carte réseau en mode "monitoring",

- La carte Wi-Fi du RPI 4 n’est **pas capable de faire du monitoring**,

- L'écran ne fonctionne qu'avec une version spéciale de Raspbian, je dois donc laisser tomber Kali,

- Le réseau du Cégep **ne permet pas la redirection de ports**.

---

- Le modèle de valise que je voulais utiliser coûte **trop cher** (250 $CAD),

- Plusieurs applications de pentesting **ne fonctionnent que sur une architecture amd64** et pas sur une architecture **arm64** (RPI),

- Plusieurs applications nécessitent de mettre la carte réseau en mode "monitoring",

---

- La carte Wi-Fi du RPI 4 n’est **pas capable de faire du monitoring**,

- L'écran ne fonctionne qu'avec une version spéciale de Raspbian, je dois donc laisser tomber Kali,

- Le réseau du Cégep **ne permet pas la redirection de ports**.

---

## Les solutions

---

- Boîtier incluant un écran sur Amazon (37 $CAD),

- **Alternatives** aux applications amd64,

- Aide du Cégep pour les composants externes, je pourrai ensuite tester les attaques avec la carte en mode "monitoring" tout en ayant un retour vidéo,

- Acheter, dans le futur, un **dongle Wi-Fi** pour le monitoring,

- Installer les **applications Kali sur Raspbian**,

- J’utilise le **LTE de mon téléphone** pour lancer l’attaque de phishing.

---

## Limites de la réalisation

---

- **L’architecture du RPI** (arm64) qui ne permet pas d’installer certaines applications,

- Je **perds l’accès à distance** si j’essaye d’activer le mode monitoring,

- La **carte Wi-Fi** du RPI 4 qui n’a **pas de mode monitoring**,

- Je n’ai **pas assez d’argent** pour acheter la valise qui aurait dû contenir le RPI,

- **L’écran tactile ne fonctionne qu’avec une version de Raspbian spécialement développée pour l’écran**,

- Puisque **le Cégep n’autorise pas la redirection de ports**, les liens pour l’attaque de phishing ne se créaient pas.

---

## Ce que j'ai appris

- **Fonctionnement d'attaques** de phishing, Evil Twin, DHCP Exhaustion, découverte de réseau,

- **Se déplacer dans un réseau et exploiter ses failles** en tant qu'attaquant,

- **Nouvelles méthodes d'attaques**,

- **Batteries** pour RPI,

- Comment **utiliser des logiciels de piratage réseau**.

---

## Sources d'information

[Liste Google Docs](https://docs.google.com/document/d/1IzLjMs-Edq09bgt-8ZZXHvkbIb2k9g3TPWagCHdaXEk/edit?usp=sharing)
