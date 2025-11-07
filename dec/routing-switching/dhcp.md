
## Exclure des adresses IP qui ne seront pas en DHCP


> [!INFO]
Les adresses qui ont été attribuées statiquement aux périphériques sur des réseaux qui utiliseront DHCP doivent être exclues des pools DHCP. Cela évite les erreurs associées aux adresses IP dupliquées. En outre, les adresses sont exclues pour l'attribution statique à d'autres périphériques tels que des serveurs et des interfaces de gestion de périphériques.

```
conf t
ip dhcp excluded-adress (adresse de début | adresse de fin)
```
## Créer un Pool

```
conf t
ip dhcp pool (nom du pool)
network (adresse IP) (masque)
default-router (adresse IP)
dns-server (adresse IP)
```
## Configurer un relai

> [!INFO]
Pour que les clients DHCP obtiennent une adresse à partir d'un serveur sur un segment LAN différent, l'interface à laquelle les clients sont attachés doit inclure une adresse d'assistance pointant vers le serveur DHCP. Dans ce cas, les hôtes sur les LAN qui sont attachés à R1 et R3 accèdent au serveur DHCP configuré sur R2. Les adresses IP des interfaces série R2 attachées à R1 et R3 sont utilisées comme adresses d'assistance. Le trafic DHCP à partir des hôtes sur les réseaux locaux de R1 et R3 sera transféré à ces adresses et traité par le serveur DHCP configuré sur R2.

```
conf t
interface (non d'interface)
ip helper-adress (adresse du DHCP)

```
## Configurer un routeur pour qu'il prenne une adresse DHCP

```
conf t
interface (nom de l'interface)
ip address dhcp
no shutdown
```
