## Calcul de sous réseaux en ligne de commande

### Installation de ipcalc
```Bash
sudo apt install ipcalc -y
```

### Informations à propos du réseau (ex: 192.168.20.0/24)
```Bash
ipcalc 192.168.20.0/24

Address:   192.168.20.0         11000000.10101000.00010100. 00000000
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.20.0/24      11000000.10101000.00010100. 00000000
HostMin:   192.168.20.1         11000000.10101000.00010100. 00000001
HostMax:   192.168.20.254       11000000.10101000.00010100. 11111110
Broadcast: 192.168.20.255       11000000.10101000.00010100. 11111111
Hosts/Net: 254
```

### Affichage sans les données en binaire
```Bash
ipcalc -b 192.168.20.100

Address:   192.168.20.100 
Netmask:   255.255.255.0 = 24   
Wildcard:  0.0.0.255            
=>
Network:   192.168.20.0/24      
HostMin:   192.168.20.1         
HostMax:   192.168.20.254       
Broadcast: 192.168.20.255       
Hosts/Net: 254                   Class C, Private Internet
```

### Afficher la classe (CIDR)
```Bash
ipcalc -c 192.25.154.38

24
```

### Afficher les informations au format HTML
```Bash
ipcalc -h 192.168.20.100 > tyty.html && firefox tyty.html
```

### Diviser une adresse réseau en plusieurs sous réseaux selon un nombre de postes donnés par réseau

#### Un exemple avec le réseau 192.168.1.0/24
- On veut 3 sous réseaux
   - Pour le premier sous-réseau on a besoin de 12 postes
   - Pour le deuxième sous-réseau on a besoin de 22 postes
   - Pour le troisième sous-réseau on a besoin de 32 postes

```Bash
$ ipcalc 192.168.1.0/255.255.255.0 -s 12 22 32 

Address:   192.168.1.0          11000000.10101000.00000001. 00000000
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.1.0/24       11000000.10101000.00000001. 00000000
HostMin:   192.168.1.1          11000000.10101000.00000001. 00000001
HostMax:   192.168.1.254        11000000.10101000.00000001. 11111110
Broadcast: 192.168.1.255        11000000.10101000.00000001. 11111111
Hosts/Net: 254                   Class C, Private Internet

1. Requested size: 12 hosts
Netmask:   255.255.255.248 = 29 11111111.11111111.11111111.11111 000
Network:   192.168.1.96/29      11000000.10101000.00000001.01100 000
HostMin:   192.168.1.97         11000000.10101000.00000001.01100 001
HostMax:   192.168.1.102        11000000.10101000.00000001.01100 110
Broadcast: 192.168.1.103        11000000.10101000.00000001.01100 111
Hosts/Net: 6                     Class C, Private Internet

2. Requested size: 22 hosts
Netmask:   255.255.255.224 = 27 11111111.11111111.11111111.111 00000
Network:   192.168.1.64/27      11000000.10101000.00000001.010 00000
HostMin:   192.168.1.65         11000000.10101000.00000001.010 00001
HostMax:   192.168.1.94         11000000.10101000.00000001.010 11110
Broadcast: 192.168.1.95         11000000.10101000.00000001.010 11111
Hosts/Net: 30                    Class C, Private Internet

3. Requested size: 32 hosts
Netmask:   255.255.255.224 = 27 11111111.11111111.11111111.111 00000
Network:   192.168.1.0/27       11000000.10101000.00000001.000 00000
HostMin:   192.168.1.1          11000000.10101000.00000001.000 00001
HostMax:   192.168.1.30         11000000.10101000.00000001.000 11110
Broadcast: 192.168.1.31         11000000.10101000.00000001.000 11111
Hosts/Net: 30                    Class C, Private Internet

Needed size:  112 addresses.
Used network: 192.168.1.0/24.999999999999999999999999999999999999999
Unused:
192.168.1.112/28
192.168.1.128/25
```