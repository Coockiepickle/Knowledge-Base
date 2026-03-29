
## Configuration PAgP
```
conf t
interface (interface à mettre en port-channel)
shutdown
channel-group (n° group) mode "auto" ou "desirable"
no shutdown
exit
```
```
interface port-channel (n° group)
switchport mode trunk
exit
```

## Configuration LACP
```
conf t
interface (interface à mettre en port-channel)
shutdown
channel-group (n° group) mode "active" ou "passive"
no shutdown
exit

interface port-channel (n° group)
switchport mode trunk
exit
```

Voir [[Modes EtherChannel]] pour savoir quel mode mettre

## Sortir un port d'un EtherChannel
```
conf t
interface (interface à sortir)
no channel-group (n° group)
exit
```

## Vérifications
```
show etherchannel summary
show interfaces trunk
show spanning-tree
```
