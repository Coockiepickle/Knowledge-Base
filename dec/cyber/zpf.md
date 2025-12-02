(Zone-based Policy Firewall, Pare-feu à politiques basées sur les zones)

# Configurer un ZPF

### Étape 1 : Créer les zones

```
conf t
zone security (nom_de_la_zone)
exit
```

### Étape 2 : Identifier le trafic

```
conf t
class-map type inspect match-any (nom_de_la_classe)
```
ou
```
conf t
class-map type inspect match-all (nom_de_la_classe)
```
puis
```
match access-group (n°_ou_nom_de_l'acl)
```
ou
```
match protocol (nom_du_protocole)
```
ou
```
match class-map (nom_du_mappage_de_classe)
```

!!! note
	*Pour le protocole, lorsqu'on autorise le trafic HTTP par exemple, il est recommandé d'inclure le trafic DNS, donc les commandes seront :*
	    match protocol http
	    match protocol https
	    match protocol dns


### Étape 3 : Définir une action

```
policy-map type inspect (nom_du_mappage_de_politiques)
class type inspect (nom_de_la_classe_de_mappage)
{inspect | drop | pass}
```
!!! note
    [Actions ZPF |Voir la définition des actions ZPF]

### Étape 4 : Identifier une paire de zones et l'associer à une politique

```
conf t
zone-pair security (nom_de_la_paire_de_zone) source (nom_de_la_source | self) destination (nom_de_la_destination | self)
service-policy type inspect (nom_de_la_politique_de_mappage)
```
### Étape 5 : Attribuer des zones aux interfaces

```
conf t
(sélectionner_interface)
zone-member security (nom_de_la_zone)
```

!!! info
	Il faut évidemment attribuer deux interfaces, par exemple une interface publique et une interface privée
