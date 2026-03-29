
### Activer AAA

```
conf t
aaa new-model
```

> [!WARNING]
> Il est recommandé de définir un nom d'utilisateur et un mot de passe sur le serveur d'accès avant de démarrer la configuration AAA, afin de ne pas être verrouillé hors du routeur.


### Spécifier le serveur AAA externe

```tacacs+
tacacs-server host (nom du serveur)
tacacs-server key (clé d'authent)
```

```radius
radius server host (nom du serveur)
radius server key (clé d'authent)
```

### Accès Exec avec AAA

```
aaa authentication login default group (radius ou tacacs+) local
```

### Accès console avec AAA

```
conf t
line con 0
exec-timeout 0
password (mot de passe)
login authentication CONSOLE
aaa authentication login CONSOLE local
```
