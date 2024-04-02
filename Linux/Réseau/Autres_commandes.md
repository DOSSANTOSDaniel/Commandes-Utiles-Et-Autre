# Réseau
## Diagnostique réseau
### La commande mtr permet d'afficher en continu les résultats d'envois de paquets avec des statistiques détaillées
```bash
mtr 8.8.8.8
```

## Affiche les adresses IP des différentes interfaces
```bash
hostname -I
```

## Test d'ouverture d'un port
### Autre méthode
```bash
(echo > /dev/tcp/127.0.0.1/22) 2> /dev/null && echo "Port en écoute" || echo "Port fermé"
```

### Exemple avec la commande scp
```Bash
$ vim scp://daniel@192.168.1.85:2244//home/daniel/exemple.txt
#           ^             ^                   ^                ^                              ^
#            |              |                    |                 |                               |
#           v              |                    |                 v                              |
# Protocole      v                    |              Port                          v
#                Hostname            v                                  Chemin du fichier
#                                IP de la machine                                          
```

### Exemple avec la commande sftp
```Bash
vim sftp://daniel@192.168.1.85//home/daniel/toto/exemple.txt
```

### Exemple avec la commande rcp
```Bash
vim rcp://daniel@192.168.1.85//home/daniel/toto/exemple.txt
```

### Exemple en HTTPS 
```Bash
vim https://daniel@192.168.1.85//home/daniel/toto/exemple.txt
```

## Afficher l'activité des services réseau en temps réel
```Bash
lsof -i
```

## Afficher les applications qui utilisent internet
```Bash
lsof -P -i -n
ss -p
```

## interface web terminal ssh(Shell In A Box)
### installation
```Bash
sudo apt install openssl shellinabox
```
* Shellinaboxd écoute sur le port 4200 en TCP : https://votre IP:4200

## Afficher les connexions actives sur un poste
Trouver les processus spécifiques en écoute sur un port.
```Bash
lsof -i TCP:80
```

Pour le trafic en TCP
```Bash
lsof -i TCP
```

Pour le trafic en UDP
```Bash
lsof -i UDP
```

Les connections établies sur un poste distant.
```Bash
lsof -i @192.168.1.22
```

## Afficher la liste des port disponibles sous Linux
```Bash
nano /etc/services
```

## Récupération de certaines informations du système avec `cat`
### Connections TCP
```bash
cat  /proc/net/tcp
```

### Connections UDP
```bash
cat  /proc/net/udp
```

### Affiche l'adresse MAC
* Interface internet a adapter(eth0)
```bash
cat /sys/class/net/eth0/address
```

### Informations sur les interfaces réseau
```bash
cat  /proc/net/route
```

### Informations sur l'interface wifi
```bash
cat  /proc/net/wireless
```

## Afficher l'activité des services réseau en temps réel
```Bash
lsof -i
```

## Afficher les applications qui utilisent internet
```Bash
lsof -P -i -n
ss -p
```