## Afficher le statut d'avancement de la commande dd

### Avec le signal USR1
```Bash
dd if=/dev/zero of=/dev/null &
```

Récupération du PID du processus
```Bash
echo $!

49484
```

Envoi un message au processus pour qu'il affiche le statut
```Bash
kill -USR1 49484
```

Tuer le processus
```Bash
kill 49484
```

### Afficher la progression avec l'option status=progress 
```Bash
dd if=/dev/zero of=/dev/null status=progress
```

### Afficher la progression avec la commande pv 
```Bash
pv /dev/zero | dd of=/dev/null bs=4M
```

## Clone USB
```Bash
lsblk
dd if=/dev/sdc of=/home/daniel/Documents/Flash_Rescue.iso bs=4M status=progress
umount /dev/sdc1
lsblk
dd if=/home/daniel/Documents/Flash_Rescue.iso of=/dev/sdc bs=4M status=progress && sync
```

Ou sans créer de fichier iso

```Bash
dd if=/dev/sdX of=/dev/sdY bs=64K status=progress conv=noerror && sync
```

Pour voir la progression aussi on peut utiliser pv
```Bash
apt install pv
lsblk
dd if=/dev/zero | pv | dd of=/dev/sdc1  bs=512
```

## Configuration optimal de DD
```Bash
sudo dd bs=4M if=/path/to/archlinux.iso of=/dev/sdx status=progress oflag=sync
```
* bs         : taille du bloc de 4mo
* oflag=sync : garantit que les données sont physiquement écrites sur la clé usb avant la fin de la commande dd
