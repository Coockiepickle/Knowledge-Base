
## Créer ACL

```interdire
conf t
access-list (n° ACL) deny (adresse IP ou réseau) (masque inversé)
```

ou

```autoriser
access-list (n° ACL) permit (adresse IP ou réseau) (masque inversé)
```

## Appliquer ACL

```sortie
conf t
int (nom de l'interface)
ip access-group (n° ACL) out
```

ou

```entrée
ip access-group (n° ACL) in
```
## Vérifications

```
show access-lists
show ip int (nom interface)
show running-config
```

### Raccourcis

```
any = tous
host = 0.0.0.0
```

### À Savoir

- ACL Standard : Plus proche de la destination
- ACL Étendue : Plus proche de la source