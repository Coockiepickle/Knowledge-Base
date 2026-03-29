
## Mot de passe local

```
conf t
enable secret (mot_de_passe)
```

## Mot de passe d'éxécution

```
conf t
line console 0
password (mot_de_passe)
login
exit
```

## Mot de passe de ligne VTY

```
conf t
line vty (n° de ligne)
password (mot_de_passe)
login
exit
```