
## Sauvegarde avec RSYNC sur le réseau
```Bash
rsync -avrz -e 'ssh -p 22' --progress --partial --stats file.txt root@192.168.1.112:/home/daniel/Images
```
