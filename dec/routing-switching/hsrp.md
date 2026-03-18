
## Configurer Routeur Principal

```
conf t
int (n°interface)
standby version 2
standby (n°grp) ip (ip virtuelle)
standby (n°grp) priority (valeur par défaut = 100, + grand = principal)
standby (n°grp) preempt
```

## Configurer Routeur Secondaire

```
conf t
int (n°interface)
standby version 2
standby (n°grp) ip (ip virtuelle)
```

## Vérifier la configuration

`show standby`

ou

`show standby brief`

Changer les passerelles par défaut

Voir [Changer Passerelle par défaut](./dec/routing-switching/change-default-gateway.md)
