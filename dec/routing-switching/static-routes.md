
### Ajouter route statique IPv4 avec distance d'administration

```
conf t
ip route {source} {destination} {forwarding} {nombre_distance}
```

### Ajouter route statique IPv6 avec distance d'administration

```
conf t
ipv6 route {source} {destination} {nombre_distance}
```

### Ajouter route flottante IPv4 avec distance d'administration

```
conf t
ip route {source} {destination} {interface} {nombre_distance}
```

### Ajouter route flottante IPv6 avec distance d'administration

```
conf t
ipv6 route {source} {destination} {nombre_distance}
```

### Vérifications

```
show ip route
show ipv6 route
```