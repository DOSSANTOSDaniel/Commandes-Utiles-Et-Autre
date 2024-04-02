## La commande ping
Indiquer le nombre de paquets ICMP à envoyer, exemple avec 5 paquets.
```Bash
ping -c 5 192.168.1.48
```

Indiquer une limite de temps pour l'envoi de l'ensemble de tous les paquets ICMP, exemple avec 3 secondes.
```Bash
ping -w 3 192.168.1.48
```
Envoi tous les paquets ICMP possibles durant 3 secondes.

Changer le temps d’intervalle entre chaque paquet ICMP envoyé, exemple avec 0.1 secondes,(0.1 secondes = 100 ms)
```Bash
ping -i 0.1 192.168.1.48
```

Changer la taille du paquet ICMP, la taille par défaut est de 64 bytes = 64 octets sur Linux et 32 octets sur Windows.
```Bash
ping -s 80 192.168.1.48
```