
## P.O.C. Damien Reynaud

---
## Sommaire

- Le but de mon ESP
- Pourquoi ?
- Ce que j'ai réalisé
- Le réseau cible
- Les attaques que j'ai choisi
- Ce qu'il me reste à faire
- Les problèmes que j'ai rencontré
- Les solutions
- Les critères de succès
- La timeline

---
## Le but de mon ESP

---
Mettre un Raspberry Pi dans un boitier incluant un **écran**, un **clavier** et **Linux** afin d'avoir un **S**ystème de **P**entesting **P**ortatif (S.P.P.) qui permet de *faire des tests de pénétration sur un réseau*.

---
## Pourquoi ?

- Tester rapidement plusieurs attaques sans avoir un ordinateur encombrant,

- Agréable d'avoir un petit système polyvalent de ce type,

- Plus de possibilités sur Linux que sur Windows,

- Discrétion 🤫🤫,

- Plaisir d'utiliser Linux et ma passion pour les RPi.

---
## Ce que j'ai réalisé

---
J'ai :
- Installé Kali Linux sur un Raspberry Pi, mis en place un accès à distance,
- Fais de nombreuses recherches sur le fonctionnement d'attaques réseau,
- Testé plusieurs types d'attaques très répandues,
- Designé un réseau de test à attaquer sur [Draw.io](https://app.diagrams.net/),
- Installé et configuré l'écran et la batterie sur le RPI,
- Réinstallé Raspbian et les applications de pentesting de Kali.

---
## Le réseau cible

![[Cégep/Images/Réseau Screenshot.png|400]]

---
## Les attaques que j'ai choisi de réaliser 

---
## Audit de sécurité

## Avec Lynis

```
sudo ./lynis audit system -Q
```

---
## 1ère attaque 

## Découverte de réseau

## Avec NMap

---
## 2ème attaque
## Capture Wi-Fi + Crack de mot de passe Wi-Fi

## Avec Aircrack-NG

[aircrack-ng | Kali Linux Tools](https://www.kali.org/tools/aircrack-ng/)

---
## Les différents modules Aircrack-NG 

### Les principaux :

1. Airmon-NG

2. Airbase-NG

3. Airodump-NG

4. Airplay-NG

5. Aircrack-NG
### Autres :

- Airdecap-NG,

- Airgraph-NG.

---
## 3ème attaque

### DHCP Exhaustion

## Avec DHCPig

[dhcpig | Kali Linux Tools](https://www.kali.org/tools/dhcpig/)

[DHCPig GitHub](https://github.com/kamorin/DHCPig)

Juste **une** commande à taper :

```
sudo dhcpig -c -v3 -l -a -i -o wlan0
```

---
## Ce qu'il me reste à faire

---

- Faire le réseau de manière physique et/ou sur Packet Tracer,
- Trouver un moyen de s'infiltrer sur le réseau avec une autre attaque :
	- Phishing ([wifiphisher | Kali Linux Tools](https://www.kali.org/tools/wifiphisher/))
	- Evil twin ([airgeddon | Kali Linux Tools](https://www.kali.org/tools/airgeddon/))

---
## Les problèmes que j'ai rencontré

---

- Le modèle de valise que je voulais utiliser coûte **trop cher** (250 $CAD),
- Plusieurs applications de pentesting **ne fonctionnent que sur une architecture amd64** et pas sur une architecture **arm64** (RPI),
- Plusieurs applications nécessitent de mettre la carte réseau en mode "monitoring",
- L'écran ne fonctionne qu'avec une version spéciale de Raspbian, je dois donc laisser tomber Kali.

---
## Les solutions

---

- Boîtier incluant un écran sur Amazon (37 $CAD),
- Une batterie (40 $CAD),
- Aide du Cégep pour les composants externes, je pourrai ensuite tester les attaques avec la carte en mode "monitoring",
- **Alternatives** aux applications amd64.

---
## Critères de succès

- Pouvoir **infiltrer** un réseau Wi-Fi,
- Pouvoir **lancer plusieurs attaques** à partir du RPI,
- Pouvoir se connecter **à distance** à Raspbian.

---
## Timeline

| Date de début  | 4ème semaine | 8ème semaine | 12ème semaine |
| -------------- | ------------ | ------------ | ------------- |
| 05 / 02 / 2024 | 10 %         | 25 %         | 60 %          |

| 14ème semaine | 17ème semaine ~ | Date de fin    |
| ------------- | --------------- | -------------- |
| 85 % (prévu)  | 100 % (prévu)   | 26 / 05 / 2024 |

---
## Est-ce que vous avez des questions ?

---

> Mmmm non

\- Fabien, 2021

