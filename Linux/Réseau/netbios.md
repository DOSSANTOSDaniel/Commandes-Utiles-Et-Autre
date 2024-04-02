## Afficher les ordinateurs possédant un nom netbios sur un réseau
```bash
sudo nbtscan -r 192.168.0.0/24
sudo nbtscan -rv 192.168.0.0/24
sudo nbtscan 192.168.0.1-254
sudo nbtscan -v -s : 192.168.1.0/24
```

## Afficher le nom netbios et le rôle d'un ordinateur
```Bash
nmblookup -A 192.168.0.17

Looking up status of 192.168.0.17
    DANIEL-PC   	<00> -     	B <ACTIVE>
    WORKGROUP   	<00> - <GROUP> B <ACTIVE>
    DANIEL-PC   	<20> -     	B <ACTIVE>
    WORKGROUP   	<1e> - <GROUP> B <ACTIVE>
```

|Rôle|Description|
|---|---|
|<00>|Station de travail.|
|<03>|Service de messagerie.|
|<20>|Serveur.|
|<1B>|Contrôleur de domaine.|
|<1C>, <1D>|Explorateur de domaine.|

Autres commandes pour scanner le réseau.
```Bash
nmap --script smb-os-discovery.nse -p445 192.168.1.0/24
```
