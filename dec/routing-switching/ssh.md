
> [!INFO]
**Secure Shell** (**SSH**) est à la fois un [programme informatique](https://fr.wikipedia.org/wiki/Programme_informatique "Programme informatique") et un [protocole de communication](https://fr.wikipedia.org/wiki/Protocole_de_communication "Protocole de communication") sécurisé. Le protocole de connexion impose un échange de [clés de chiffrement](https://fr.wikipedia.org/wiki/Cl%C3%A9_de_chiffrement "Clé de chiffrement") en début de connexion. Par la suite, tous les [segments](https://fr.wikipedia.org/wiki/Couche_transport "Couche transport") [TCP](https://fr.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") sont authentifiés et chiffrés. Il devient donc impossible d'utiliser un _[sniffer](https://fr.wikipedia.org/wiki/Sniffer "Sniffer")_ pour voir ce que fait l'utilisateur.

>[!INFO]
Le protocole SSH a été conçu avec l'objectif de remplacer les différents protocoles non chiffrés comme [rlogin](https://fr.wikipedia.org/wiki/Rlogin "Rlogin"), [telnet](https://fr.wikipedia.org/wiki/Telnet "Telnet"), [rcp](https://fr.wikipedia.org/wiki/Rcp_(Unix) "Rcp (Unix)") et [rsh](https://fr.wikipedia.org/wiki/Rsh "Rsh").

## Comment activer le SSH et désactiver Telnet

```
en
conf t
username nom_utilisateur privilege 15 secret mot_de_passe
end
line vty 0 15
no password
login local
transport input ssh
end
exit
wr
```