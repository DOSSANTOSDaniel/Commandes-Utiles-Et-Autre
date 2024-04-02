## Gestionnaire de paquets windows winget

### installation
https://translate.google.com/website?sl=auto&tl=fr&hl=fr&u=https://github.com/microsoft/winget-cli/releases/

## Utilisation de Winget pour la gestion des applications

### Recherches d'applications
```Powershell
winget search chrome
```

### Installation d'une application
```
winget install balenaEtcher
```

### Mise à jour d'une application
```
winget upgrade Google.Chrome
```

### Désinstallation d'une application
```
winget uninstall Google.Chrome
```

### Afficher des informations sur une application
```
winget show --name Vim
```

### Lister les applications installées
winget list

## Lister les sources (dépôts)
msstore. Le référentiel Microsoft Store.
winget. Le référentiel de logiciels Winget est géré par Microsoft.
```Powershell
winget source list
```

### Ajouter une source
```Powershell
winget source add --name [name] [url]
```

### Mise à jour des sources
```Powershell
winget source update
```

### Réinitialiser winget
```Powershell
winget source reset --force
```

## gestionnaire de paquets windows chocolatey ou choco

Changer la politique d'exécution des scripts 
```Powershell
Set-ExecutionPolicy Bypass -Scope Process
```

Installation de chocolatey
```Powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

Installer une application
```Powershell
choco install vim
```

Mise à jour d'une application
```Powershell
choco upgrade vim
```

Mise à jour de toutes les applications
```Powershell
choco upgrade all
```

Rechercher une application
```Powershell
choco search package-name
```

Lister les applications installées
```Powershell
choco list
```

Interface graphique pour choco
```Powershell
choco install chocolateygui
```
https://orcacore.com/install-chocolatey-choco-windows/

## Gestionnaire de paquets scoop pour windows

Configurer la politique d’exécution
Remotesigned permet d'executer des scripts créé par moi ou téléchargé sur internet
```Powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Télécharger scoop et installation
```Powershell
Invoke-Expression "& {$(Invoke-RestMethod get.scoop.sh)} -RunAsAdmin"
```

Afficher l'aide 
```Powershell
scoop -h
```

Lister les dépôts disponibles
```Powershell
scoop bucket list
```

Recherche une application
```Powershell
scoop search package-name
```

Installer une application
```Powershell
scoop install 7zip
```

Mise à jour des paquets
```Powershell
scoop update
scoop update package-name
scoop update *
```

Afficher le statu
```Powershell
scoop status
```

Lister les dépôts possibles a ajouter
```Powershell
scoop bucket known
```

Ajouter des dépôts
```Powershell
scoop bucket add java
```

Utiliser une autres version d'une application 
```Powershell
scoop reset openjdk
```

