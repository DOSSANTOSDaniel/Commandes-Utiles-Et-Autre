## Sauvegarde d'un périphérique dans un fichier sur un poste distant via SSH
```Bash
dd if=/dev/sda | ssh daniel@192.168.1.22 'dd of=sda.img'
```