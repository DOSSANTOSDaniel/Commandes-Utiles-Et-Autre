# Pare-feu

## Désactiver et activer le Pare-feu
```Powershell
netsh advfirewall set allprofiles state off
netsh advfirewall set allprofiles state on
```

## Gérer le pare-feu de Windows avec Powershell
Voir toutes les variables d’environnement.
```Powershell
dir env:
```

Créer une règle basée sur Les groupes de règles prédéfinies.
```Powershell
New-NetFirewallRule –DisplayName "Autoriser le Bureau à distance (RDP)" -Group "Bureau à distance" -Profile Domain -Enabled True -Action Allow
```

Déterminer si le pare-feu est activé ou non.
```Powershell
get-netfirewallprofile | Format-Table name,enabled
```

Activer le pare-feu.
```Powershell
set-netfirewallprofile -profile domain,public,private -enabled true
```
Ou
```Powershell
set-netfirewallprofile -profile * -enabled true
```

Désactiver le pare-feu.
```Powershell
set-netfirewallprofile -profile domain,public,private -enabled false
```

Exemple:
```Powershell
new-netfirewallrule -name "SSH" -displayname "SSH serveur" -profile domain,public,private -enabled true -protocol TCP -localport 22 -Action allow
new-netfirewallrule -name "LogicBackup" -displayname "LogicBackup, Port 873" -profile domain,public,private -enabled true -protocol TCP -localport 873 -Action allow
```

## Autoriser le ping sur Windows serveur
Windows serveur par défaut n’autorise pas le ping.
```Powershell
netsh advfirewall firewall add rule name="ICMP Allow" protocol="icmpv4:8,any" dir=in action=allow
```
## Afficher des informations
```Powershell
netsh advfirewall show
```

## Afficher les règles du pare-feu
```Powershell
get-netfirewallrule
```

Rechercher une règle en particulier
```Powershell
get-netfirewallrule -DisplayName *SSH*
```
