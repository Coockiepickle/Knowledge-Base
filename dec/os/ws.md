
# Ajouter disque dur


### CMD

```
diskpart
list disk
select disk (n° disque)
detail disk
attributes disk
attributes disk clear readonly
```

Menu Démarrer > Outils d'administration > Gestion de l'ordinateur > Stockage > Gestion des disques (on est censé voir un message pour initialiser le disque)


# Ajouter emplacement réseau

## Powershell

net use (lettre_pas_utilisée): \\NOMSERVEUR\chemin

### Supprimer emplacement

net use (lettre): /delete


## Ajouter Utilisateur CMD

```
dsadd user "cn=Nom Complet,ou=Prog,ou=LaPocatiere,dc=MONSERV,dc=local" -fn Prénom -ln Nom -display "Nom Complet" -disabled no -upn pnom@MONSERV.local -samid pnom -pwd password -mustchpwd no -pwdneverexpires yes -memberof cn=Direction,cn=Users,dc=MONSERV,dc=local
```

## Modifier autorisations CMD

[ICACLS Microsoft](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753525(v=ws.10)?redirectedfrom=MSDN)

