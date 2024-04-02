## Scanner un réseau privé sans NMAP

Installation de arp-scan
```Bash
apt-get install arp-scan
```

Lancement du scan sur le réseau local
```Bash
arp-scan --interface=<interface réseau> --localnet
```

## Quelques commandes NMAP
* Scan des 1000 ports les plus utilisés.
* L’option "-Pn" est conseillé car elle désactive la découverte des hôtes et oblige Nmap à
scanner chaque système comme s’il était actif.
```Bash
nmap -sC -sV -Pn 192.168.1.35
```

Pour effectuer un scan sur l’intégralité des ports il faut ajouter l’option "-p-"
```Bash
nmap -sC -sV -Pn -p- 192.168.1.35
```

Afficher les machines connectées sur le réseau
```Bash
nmap -sn 192.168.1.0/24
```

## Contourner un firewall avec nmap
```
nmap 192.168.1.22 -sS -Pn -n --disable-arp-ping --packet-trace --source-port 53
                	^   ^  ^       	^           	^            	 	^
            Un scan SYN |  |       	|           	|            	 	|
       Eviter paquets icmp request  |            	|           	 	|
                	       |       	|           	|            	 	|
              Pas de résolution dns |               |                	|             	 
                          	Désactiver le ping arp  |                   |
                                     Tracer les paquets envoyé par nmap |											                            |
                                                        Utiliser le pour 53 pour envoyer les requêtes nmap
```

## Scanner en utilisant la commande arp-scan
```Bash
for i in 192.168.1.{1..80}; do ping -c 1 -W 1 $i > /dev/null && (echo "IP: $i" && echo "NAME : $(host $i | awk '{print $NF}')" && echo "OTHER : $(sudo arp-scan $i | sed -n '3p')" && echo "-----------------------------------") ; done
```

## Détection d’un conflit d’adresses IP dans un réseau

### Alimenter la table ARP
Normalement il faudrait faire un ping de diffusion broadcast pour alimenter la table ARP mais la plupart des machines sous Linux ignorent le ping broadcast(cat /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts).

On va donc faire un ping manuel sur chaque machine du réseau avec deux méthodes.
1. Utiliser la commande ping (~5 minutes). 
```Bash
for i in 192.168.1.{1..254}; do ping -n -c 1 -W 1 $i; done
```
* La commande tcpdump pour visualiser l'envoi de paquets icmp sur le réseau.
```Bash
sudo tcpdump -i enp1s0 icmp
```
2. Utiliser la commande arp-scan (~3 secondes).
```Bash
sudo arp-scan -I enp1s0 -l
```

## Scanner le réseau local et afficher le nom et l'adresse IP des machines connectées
```Bash
for i in 192.168.1.{1..254}; do ping -c 1 -W 1 $i > /dev/null && (echo "IP: $i" && echo "NAME : $(host $i | awk '{print $NF}')" && echo "-----------------------------------") ; done
```

### En utilisant la commande arp-scan
```Bash
for i in 192.168.1.{1..80}; do ping -c 1 -W 1 $i > /dev/null && (echo "IP: $i" && echo "NAME : $(host $i | awk '{print $NF}')" && echo "OTHER : $(sudo arp-scan $i | sed -n '3p')" && echo "-----------------------------------") ; done
```

Scanner le réseau pour trouver les machines avec nom netbios.
```Bash
nmap --script smb-os-discovery.nse -p445 192.168.1.0/24
```

