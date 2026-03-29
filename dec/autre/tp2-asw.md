
> [!IMPORTANT]
> J'ai réalisé cette doc avec Obsidian, or, MarkDown Viewer ne permet pas d'afficher ce bloc de manière :sparkles: jolie :sparkles:, je recommande donc de l'ouvrir avec Obsidian

---

## Paramètres réseau

Dans **SConfig**, entrer ==8==, puis le numéro de la carte réseau que l'on veut modifier, ensuite, entrer ==1==, choisir ==(S)== puis rentrer la configuration IP :

- Adresse IP,
- Masque de sous-réseau,
- Passerelle par défaut

#### Sinon, en ligne de commande :
```
Get-NetIPAddress
```
Noter le numéro d'interface, puis :
```
New-NetIPAddress -Interface-Index <n° de l'interface> -IPAddress <Adresse IP> -PrefixLength 24 -DefaultGateway 100.0.0.1
```

#### Modifier le DNS

Entrer ==8==, puis le numéro de la carte réseau que l'on veut modifier, ensuite, choisir ==2==, puis entrer l'adresse IP du contrôleur de domaine pour les machines **IIS** et **DB**.

---

## Mettre à jour la VM

Dans **SConfig**, entrer ==6==, puis ==1==, ensuite, attendre que les mises à jour se télécharge et répondre ==(O)==ui pour installer toutes les mises à jour, on attend encore et on redémarre si nécessaire.

---

## AD-DS

```PowerShell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools

Import-Module ADDSDeployment

Install-ADDSForest -DomainName infodec.quebec -InstallDNS
```

> [!IMPORTANT] 
> Rentrer le mot de passe administrateur 2 fois, choisir "Oui" quand un choix apparaît et attendre le redémarrage


---

## RAID-1


``diskpart``
```Powershell
select disk 1
convert dynamic

select disk 2
convert dynamic

create volume mirror disk=1,2

select volume 0
format fs=ntfs label="IISWebSites" quick
assign letter=W
```

---

## Installation MariaDB

```PowerShell
.\mariadb-11.3.2-winx64.msi
```
Cocher la case :
"Enable root access..."

Chemin des datas :
"S:\data"

---

## Installation IIS

```PowerShell
Install-WindowsFeature Web-Server -IncludeManagementTools
```

> [!WARNING]
> Après chaque modification, taper la commande `iisreset`

---

## Installation PHP

```PowerShell
Install-WindowsFeature Web-CGI
```

Lancer l'installation de **VC_redist.X64.exe**

Redémarrer le serveur

```PowerShell
Expand-Archive -LiteralPath 'Z:\php-8.3.3-nts-Win32-vs16-x64.zip' -DestinationPath C:\PHP

cp php.ini-development php.ini

notepad.exe C:\PHP\php.ini


New-WebHandler -Name "PHP-FastCGI" -Path "*.php" -Verb "*" -Modules "FastCgiModule" -ScriptProcessor "c:\php\php-cgi.exe" -ResourceType File

notepad.exe C:\Windows\System32\inetsrv\config\applicationHost.config

<fastCgi>  
	<application fullPath="C:\PHP\php-cgi.exe" monitorChangesTo="C:\PHP\php.ini"> 
		<environmentVariables>  
			<environmentVariable name="PHPRC" value="C:\PHP\" />  
			<environmentVariable name="PHP_FCGI_MAX_REQUESTS" value="10050" />  
		</environmentVariables>  
	</application>  
</fastCgi>
```

Puis, entrer la commande :
`iisreset`

---

## Installation PHPMyAdmin

```Powershell
Expand-Archive -LiteralPath 'Z:\phpMyAdmin-5.2.1-all-languages.zip' -DestinationPath C:\inetpub\wwwroot
```
Décommenter, dans `php.ini` à la ligne 770 environ :

```
extension_dir = "ext"
```

et, à la fin du fichier, rajouter :

```
extension = "mysqli"
extension = "mbstring"
```

Rendre la machine accessible sur internet, en choisissant "Accès par pont" dans VirtualBox et installer IIS dans WAC.

```PowerShell
Rename-Item C:\inetpub\wwwroot\phpMyAdmin-5.2.1-all-languages phpMyAdmin
```

Dans le fichier `C:\Windows\System32\inetsrv\config\applicationHost.config`
```PowerShell
directoryBrowse enabled="true"
<add value="index.php" />
```

Copier le fichier `config.sample.inc.php` en `config.inc.php`

```
icacls.exe "C:\inetpub\wwwroot\phpMyAdmin" /grant "IIS_IUSRS:(OI)(CI)F"
```

Se rendre sur `100.0.0.20/phpmyadmin/config.inc.php` pour vérifier que tout va bien.

On peut maintenant se login sur [phpMyAdmin](https://100.0.0.20/phpmyadmin)


---

## Création du site Arcadia

```PowerShell
mkdir W:\arcadia

Expand-Archive -LiteralPath 'Z:\Joomla_5.0.3-Stable-Full_Package.zip' -DestinationPath W:\arcadia

New-IISSite -Name "arcadia" -BindingInformation "*:80:arcadia.lcal" -PhysicalPath "W:\arcadia" -Passthru

New-WebAppPool -Name "arcadia"

Import-Module WebAdministrator

iis:

Set-ItemProperty IIS:\Sites\arcadia\ -Name ApplicationPool -Value arcadia

Start-IISSite arcadia

icacls "W:\arcadia" /grant "IIS_IUSRS:(OI)(CI)F"
```
On peut maintenant accéder à [Joomla](https://arcadia.local) et suivre les instructions d'installation.

---

## Création du site Antares

```PowerShell
mkdir W:\antares

Expand-Archive -LiteralPath 'Z:\wordpress-6.4.3-fr_FR.zip' -DestinationPath W:\antares

New-IISSite -Name "antares" -BindingInformation "*:80:antares.local" -PhysicalPath "W:\antares" -Passthru

New-WebAppPool -Name "antares"

Import-Module WebAdministrator

Set-ItemProperty IIS:\Sites\antares\ -Name ApplicationPool -Value antares

Start-IISSite antares

icacls "W:\antares" /grant "IIS_IUSRS:(OI)(CI)F"
```

On peut maintenant accéder à [Wordpress](https://antares.local) et suivre les instructions d'installation.

> [!TIP] Pour voir les images
> `<mimeMap fileExtension=".webp" mimeType="image/webp" />`

---

## Création des utilisateurs

1. Lancer WAC

2. Cliquer sur "Créer" et choisir "Utilisateur"

| Nom          | Nom de compte SAM | Mot de passe |
| ------------ | ----------------- | ------------ |
| antaresuser  | antaresuser       | asw@2024     |
| arcadiauser  | arcadiauser       | asw@2024     |
| antaresuser2 | antaresuser2      | asw@2024     |
| arcadiauser2 | arcadiauser2      | asw@2024     |

3. Cliquer sur "Créer"

---

>[!QUESTION]- Auteur
>Documentation réalisée par Damien Reynaud le 22 Mars 2024


