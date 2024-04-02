## Afficher la progression de la copie
```bash
dd if=/dev/zero | pv | dd of=/dev/sdc1  bs=512
```

## Création d'une image disque
```bash
dd if=/dev/sda1 conv=sync,noerror status=progress bs=128K | gzip -c > image.gz
```
### Copie sur un nouveau disque 
```bash 
gunzip -c image.gz | dd of=/dev/sdb1
```
### Création d'une image disque sur une machine distante
```bash 
dd if=/dev/sda1 conv=sync,noerror status=progress bs=128K | gzip -c | ssh daniel@192.168.1.48 dd of=image.gz
```

## Graver un fichier ISO
```Bash
dd if="file.iso" of="/dev/sdc" status="progress" conv="fsync"
```
|Option|Description|
|---|---|
|conv="fsync"|Synchronise les données pour une finalisation correcte, s'assure que l'intégralité de l'iso a été écrite sur le périphérique.|
|status="progress"|Affiche l'avancement du transfère, temps restant avant la fin.|

* BS= 512 (default), 4096 (4K), 65536 (64K), 1048576 (1M), 4194304 (4M)
```Bash
  dd if=image.iso | pv | dd of=/dev/sdb bs=4M oflag=sync
```

```Bash
sudo dd if=sdcard_image.img of=/dev/sdb bs=4M conv=fsync status=progress
```

## On peut monter une iso aussi ainsi
```Bash
mount xxxx.iso /mnt -t iso9660 -o loop
```
