## Afficher le contenu du cache DNS (systemd)
- C'est l'alternative à la commande 'ipconfig /displaydns' sur Windows.
### Libérer les informations du cache DNS
- Quand systemd-resolved reçoit le signal USR1, il va rendre accessible les informations des enregistrements du cache DNS dans les journaux du système.
```Bash
sudo systemctl kill --signal='USR1' systemd-resolved
```

### Affichage du contenu du cache DNS
```Bash
sudo journalctl -b -u systemd-resolved --grep=" IN " --no-pager --no-hostname
```

|Option|Description|
|---|---|
|-b|Les journaux depuis le démarrage courant seront affichés, pour tous les démarrages '-b all'.|
|--grep=" IN "|Recherche l'occurrence  " IN ".|
|--no-pager|Mode non interactif, par défaut cela utilise less pour afficher les données.|
|--no-hostname|N'affiche pas le hostname de la machine.|

### Effacer le contenu du cache DNS
- C'est l'alternative à la commande 'ipconfig /flushdns' sur Windows
```Bash
sudo systemd-resolve --flush-caches
```