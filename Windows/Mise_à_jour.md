# Mise à jours 

## Mettre à jour Windows
PSWindowsUpdate est un ensemble de commandes permettant de gérer le client Windows Update.
Installation de PSWindowsUpdate.
```Powershell
find-Module PSWindowsUpdate
Install-Module -Name PSWindowsUpdate -Force
Import-Module PSWindowsUpdate
```

Afficher les commandes possibles.
```Powershell
Get-Command -Module PSWindowsUpdate
```

Afficher les mises à jours disponibles.
```Powershell
Get-WindowsUpdate
```

Installation des mises à jours disponibles.
```Powershell
Install-WindowsUpdate -AcceptAll -AutoReboot
```

Avec la création de logs.
```Powershell
Install-WindowsUpdate -AcceptAll -Install -AutoReboot | Out-File "c:\logs\$(get-date -f dd-MM-yyyy_HH-mm)-WinMSJ.log" -force
```

Installation d'une mise à jour en particulier.
```Powershell
Get-WindowsUpdate -KBArticleID "KB1234567" -Install
```

Ne pas installer une mise à jour en particulier.
```Powershell
Install-WindowsUpdate -NotKBArticle "KB1234567" -AcceptAll
```

## Mise à jour windows avec winget
```Powershell
winget upgrade
winget upgrade -h --all
winget upgrade --all --include-unknown
```

## Afficher l'historique des mises à jours
```
wmic qfe list
```

## Mettre à jour ses drivers
PnPUtil.exe est un outil permettant la mise à jour des drivers.

Lister les paquets des pilotes.
```Powershell
pnputil /enum-drivers
```

Scanner les composants.
```Powershell
pnputil \scan-devices \async
```

Lister les périphériques connectés
```Powershell
pnputil /enum-devices /connected
```