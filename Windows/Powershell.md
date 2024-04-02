# Powershell

## Mise à jour de powershell sur Windowns serveur
```Powershell
Invoke-WebRequest -Uri https://github.com/PowerShell/PowerShell/releases/download/v7.3.7/PowerShell-7.3.7-win-x64.msi -OutFile PowerShell-7.3.7-win-x64.msi
.\PowerShell-7.3.7-win-x64.msi
```

## Configurer powershell 7 comme shell par défaut à la connexion SSH
```Powershell
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Program Files\PowerShell\7\pwsh.exe" -PropertyType String -Force
```

## Exécuter un script Powershell
Coller le script dans C:\WINDOWS\system32.
Exécuter Powershell en tant qu'administrateur.

Activation de l'autorisation d'exécuter des scripts sur le poste.
```Powershell
set-executionpolicy -executionpolicy unrestricted -Force
```

Exécuter le script.
```Powershell
.\script.ps1
```

Ou

```Powershell
powershell -ExecutionPolicy ByPass -File script.ps1
```

Restreindre l'autorisation d'exécuter des scripts sur le poste
```Powershell
set-executionpolicy -executionpolicy restricted -Force
```

## Commandes utiles Powershell
Lancer une commande en tant qu'administrateur
```Powershell
powershell Start-Process powershell -Verb runAs
```

Télécharger un fichier à partir d'un site web
```Powershell
Invoke-WebRequest -Uri https://aka.ms/wsl-kali-linux-new -OutFile Kali-linux.appx -UseBasicParsing
```
ou
```Powershell
curl.exe -L -o ubuntu-2004.appx https://aka.ms/wsl-ubuntu-2004
```

Renommer un fichier
```Powershell
Rename-Item .\Ubuntu.appx .\Ubuntu.zip
```

Décompresser un fichier ZIP
```Powershell
Expand-Archive .\Ubuntu.zip .\Ubuntu
```

## Équivalent a grep sur Windows
```Powershell
find <occurrence de recherche>
```

## Politique d’exécution
Accepte tout : bypass
Utilisateur courant : currentuser

```Powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser
```

Afficher des informations
```Powershell
Get-ExecutionPolicy
```

Liste des politiques d'exécution
```Powershell
Get-ExecutionPolicy -List
```

## Rétablir les règles de base de la politique d'exécution 
```Powershell
Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope CurrentUser
```

## Changer la politique d'exécution que pour un processus en particulier
```Powershell
set-ExecutionPolicy -scope Process
```

## Autres commandes powershell
Créer un nouveau fichier
```Powershell
New-Item -Path "C:\example.txt"
```

Supprimer un fichier
```Powershell
Remove-Item -Path "C:\example.txt"
```

Copier un fichier
```Powershell
Copy-Item -Path "source_path" -Destination "destination_path"
Copy-Item -Path "C:\source\directory" -Destination "D:\destination" -Recurse
```

Déplacer un fichier
```Powershell
Move-Item -Path "source_path" -Destination "destination_path"
Move-Item -Path "C:\source\directory" -Destination "D:\destination" -Recurse
```

Affiche le contenue du fichier(cat) 
```Powershell
Get-Content -Path "C:\example.txt"
```

Supprimer le contenu d’un fichier
```Powershell
Clear-Content -Path "C:\example.txt"
```

Afficher l’historique
```Powershell
Get-History
```

Lister les commandes 
```Powershell
get-command
```

Afficher l'aide
```Powershell
Get-Help Get-Service
Get-Help Get-Service -Detailed
```
