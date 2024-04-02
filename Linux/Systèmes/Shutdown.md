## Arrêter et redémarrer un système Linux
Quand on utilise la commande shutdown, tous les users reçoivent un message de broadcast

Eteindre dans 60s
```Bash
shutdown -h
```

Eteindre direct
```Bash
shutdown -h now
```
-h : halt

Reboot à 22h
```Bash
shutdown -r 22:00
```
-r : reboot

Reboot dans 5min
```Bash
shutdown -r +5
```

Afficher les programmations de reboot ou off
```Bash
sudo shutdown --show
```

Annuler une programmation d'extinction
```Bash
shutdown -c
```
-c : cancel

Programmation d'extinction sans avertissement
```Bash
shutdown -h +5 --no-wall
```

Avec un message personnel
```Bash
shutdown -h +5 --no-wall
```
```Bash
wall "On reboot dans 5 minutes!"
```
