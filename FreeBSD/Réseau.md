## Quelques trucs réseau sur freebsd
Voir le trafic arp
```bash
tcpdump 'arp'
```

Voir le trafic du port 22
```bash
tcpdump port 22
```

Ecrire dans un fichier
```bash
tcpdump -w output.pcap port 22
```

### Gestion des paquets
Ports, désigne les programmes proposés par le système de paquetage,
on parle de système de ports et pas sytème de paquetages

### Installation de freeBSD
Le programme qui démarre l'installation est `bsdinstall`

Ajouter daniel au groupe wheel
```bash
pw groupmod wheel -m daniel
```

### Configurer sudo
```bash
visudo
```

Décommenter cette ligne
```bash
%wheel ALL=(ALL:ALL) ALL
```

Afficher les ports en écoute
```bash
sockstat -4 -l
```