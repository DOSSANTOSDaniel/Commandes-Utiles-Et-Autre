## Afficher les informations sur la connexion wlan
```
netsh wlan show interfaces
```

## Afficher les mots de passes wifi

### Afficher les réseaux wifi
```Powershell
netsh wlan show profiles
```
Pour afficher tous les réseaux wifi autour de vous.
```Powershell
  netsh wlan show all
```

### Pour chacun, afficher le mot de passe
```Powershell
netsh wlan show profile name="Nom SSID" key=clear
```

### Récupération du mot de passe wifi avec l'interface graphique 
Commande pour ouvrir le centre de réseau et partage > (ncpa.cpl) > faire un clique droit sur statut > propriétés sans fil > sécurité.