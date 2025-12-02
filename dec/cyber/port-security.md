
### Activer la sécurité des ports
```
conf t
interface (nom_de_l'interface)
switchport port-security
```

!!! info
    La sécurité des ports ne peut être activée que sur les interfaces en mode access


### Définir le nombre d'appareil maximum par port
```
switchport port-security maximum (nombre_d'appareils_maximum)
```

### Apprendre l'adresse MAC du périphérique
```
switchport port-security mac-address sticky
```

### Définir l'action en cas de détection de violation
```
switchport port-security violation {shutdown | restrict | protect}
```

### Désactiver tous les autres ports
```
conf t
interface range (plage_d'interfaces)
shutdown
```

### Vérification de la configuration
```
show port-security
show port-security address
show port-security interface (nom_de_l'interface)
show run | begin interface (nom_de_l'interface)
```
