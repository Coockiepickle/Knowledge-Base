# Installer une application `.tar.gz` sous Linux

!!! info "A quoi sert cette doc ?"
    Ce guide détaille comment installer facilement une application au format `.tar.gz` et comment l’ajouter au menu des applications. PyCharm sert d’exemple, mais la même méthode fonctionne pour une grande partie des applications.

!!! info "Pourquoi cette doc ?"
    L'installation d'une application sous Linux est très différente de Windows, où la plupart utilisent un simple `.exe` ou un `Install Wizard Shield`. Quand j'ai commencé à utiliser Linux, j'ai eu l'impression que cette procédure était logique pour tout le monde sauf pour moi, et était donc très souvent succinte ou mal expliquée. J'ai donc décidé d'écrire cette doc pour que cette situation devienne, en effet, logique et sans flou.

!!! warning "Attention :"
    J'ai utilisé un PC sous CachyOS avec Noctalia lors de l'écriture, l'installation peut varier selon la distribution, le shell et l'environnement de bureau !

## 1. Télécharger l’archive

Télécharger la version Linux de l’application depuis son site officiel. Le fichier se trouve généralement dans `~/Downloads`.

Vérification :
```bash
❯ ls ~/Downloads
.rw-r--r-- 1,3G - app-1.0.0.tar.gz
```


## 2. Extraire l’application

Les logiciels installés manuellement peuvent être placés dans `/opt`. Ouvrir un terminal, puis :

```bash
cd ~/Downloads
sudo tar -xzvf app-1.0.0.tar.gz -C /opt
```

- `tar -xzf` extrait l’archive. `v` est optionnel si on souhaite afficher les fichiers en cours d'extraction (`verbose`).
- `-C /opt` choisit `/opt` comme dossier de destination.
- `sudo` est nécessaire pour écrire dans `/opt`.

Vérifier le nom du dossier créé :

```bash
❯ ls /opt
drwxr-xr-x - root 21 janv.  1970 - app-1.0.0
```

## 3. Identifier et tester le lanceur

Entrer dans le dossier de l’application et regarder son contenu :

```bash
ls /opt/app-1.0.0
```

Le lanceur se trouve souvent dans un dossier `bin/`. Il peut être un script `.sh` ou un binaire sans extension.

Exemples :

```bash
/opt/app-1.0.0/bin/appl.sh
```

```bash
/opt/app-1.0.0/bin/app
```

Si le fichier n’est pas exécutable :

```bash
sudo chmod +x /opt/app-1.0.0/bin/app
```

!!! warning "Important :"
    Tester le lancement de l'application dans le terminal avant de créer le raccourci

## 4. Créer une entrée dans le menu

Les environnements de bureau Linux utilisent des fichiers `.desktop` pour afficher une application dans le launcher.

Créer le dossier personnel des raccourcis, puis le fichier :

```bash
mkdir -p ~/.local/share/applications
nano ~/.local/share/applications/app.desktop
```

Ajouter ce contenu en adaptant les chemins :

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=Nom de l'App
Comment=Description courte de l’application
Exec=/opt/app-1.0.0/bin/app
Icon=/opt/app-1.0.0/icon.png
Terminal=false
Categories=Utility;
StartupNotify=true
```

Enregistrer avec `Ctrl+S`, puis quitter `nano` avec `Ctrl+X`.

### Champs importants

- `Name=` : nom affiché dans le menu.
- `Exec=` : chemin complet vers le lanceur de l’application.
- `Icon=` : chemin complet vers l’icône. Supprimer cette ligne si aucune icône n’est fournie.
- `Terminal=false` : l’application se lance sans terminal.
- `Categories=` : catégorie utilisée par le menu.

!!! danger "Attention :"
    `Version=` ne correspond pas à la version de l'application, mais à la version de la spécification Desktop Entry.
    À ne pas confondre avec : `X-AppVersion=3.2.1`
    Cette clé est une extension non standard et peut servir à indiquer la version de l’application, mais elle n’est pas nécessaire au fonctionnement du fichier .desktop.

!!! info 
    Ne pas utiliser `~` dans `Exec=` ou `Icon=`. Utiliser uniquement des chemins absolus

## 5. Vérifier le raccourci

Vérifier la syntaxe du fichier :

```bash
desktop-file-validate ~/.local/share/applications/app.desktop
```

S’il n’y a aucun message, le fichier est valide. L’application devrait ensuite apparaître dans le launcher.

!!! note
    Si elle n’apparaît pas immédiatement, fermez puis rouvrez le menu des applications, ou reconnectez-vous à votre session.

---

## Exemple rapide : PyCharm

Après avoir téléchargé l’archive PyCharm sur [le site officiel](https://www.jetbrains.com/pycharm/download/?section=linux) :

```bash
ls ~/Downloads
```
![Downloads](/img/downloads.png)

Extraire l'archive :
```bash
sudo tar -xzf pycharm-*.tar.gz -C /opt
```

Repérer le dossier créé :

```bash
ls /opt | grep -i pycharm
```

Démarrez PyCharm une première fois, en adaptant le nom du dossier :

```bash
/opt/pycharm-2026.2.1/bin/pycharm
```

PyCharm propose de créer automatiquement son raccourci, pour ce faire, dans PyCharm, choisir :

```text
Tools → Create Desktop Entry…
```

Puis cliquer sur `OK`

Vérifier ensuite dans le menu des applications que PyCharm apparaît.

---

Sinon, il est possible de créer le raccourci manuellement avec ce fichier officiel :

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=PyCharm
Comment=The Only Python IDE you need
Exec="/opt/pycharm-2026.2.1/bin/pycharm" %f
Icon=/opt/pycharm-2026.2.1/bin/pycharm.svg
Terminal=false
Categories=Development;IDE;
StartupWMClass=jetbrains-pycharm
StartupNotify=true
```

!!! info
    Remplacer `pycharm-2026.2.1` par le vrai nom du dossier présent dans `/opt`, correspondant à la version installée.