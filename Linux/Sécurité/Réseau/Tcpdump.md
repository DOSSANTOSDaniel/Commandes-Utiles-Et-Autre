## Capturer des événement sur le réseau avec TCPdump
TCPdump est un outil d’écoute du réseau, il permet de capturer les événement sur le réseau, on peut
aussi enregistrer la capture dans un fichier compatible avec Wireshark.
Si on tape la commande tcpdump sans aucune option, cela va écouter sur l’ensemble du réseau tout
le trafic.

Exemple d’une ligne de résultat:
```Bash
14:19:02.843122 IP L875-10E.36343 > dns.google.domain: 25395+ PTR? 22.1.168.192.in-addr.arpa. (43)
```
* Chaque ligne représente la transmission d’un paquet.

||Description|
|---|---|
|14:19:02.843122|Heure d'arrivée du paquet sur l'interface réseau|
|IP|Type de protocole TCP, UDP, IGMP, ARP, ...|
|L875-10E|adresse source.|
|.36343|port source.|
|dns.google.domain|adresse de destination.|
|25395+|Port de déstination.|
|PTR?|Type de requête, ping,DNS,HTTP,FTP?PTR...|

Écouter le réseau avec TCPdump
```Bash
tcpdump -i enp1s0 -t icmp
```

Ecouter sur une interface
```Bash
tcpdump -i enp1s0
```

Voir toutes les interfaces
```Bash
tcpdump -D
```

Voir uniquement le trafic icmp
```Bash
tcpdump icmp
```

Filtrer les paquets par source et destination
```Bash
tcpdump src 192.168.1.10
tcpdump dst 192.168.1.15
```

Afficher le contenu des paquets en representation ascii et hexa
```Bash
tcpdump -X
```

Enregistrer dans un fichier
```Bash
tcpdump -w mespaquets.pcap
```

Lire le fichier
```Bash
tcpdump -r mespaquets.pcap
```

Capturer seulement les 100 premiers octets d'un paquet
```Bash
tcpdump -s 100
```

Format de l'horodatage plus lisible
```Bash
tcpdump -tttt
```

Créer un filtre excluant
```Bash
sudo tcpdump not port 53
```