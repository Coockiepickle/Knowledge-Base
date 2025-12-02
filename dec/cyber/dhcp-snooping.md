
### Activer surveillance DHCP

```
conf t
ip dhcp snooping
```

### Truster une interface pour le DHCP

```
conf t
interface (nom_de_l'interface)
ip dhcp snooping trust
```

### Limiter le nombre de DHCPDiscover

```
conf t
interface (nom_de_l'interface)
ip dhcp snooping limit rate (nombre_de_packets_maximum_par_seconde)
```

### Activer la surveillance DHCP par VLAN

```
conf t
ip dhcp snooping (vlan)
```