## Affiche l’occupation des disques

### Commandes :
* `df -h`
* `dfc`
* `pydf`

## Commande permettant l'affichage et la gestion de l’occupation du disque
```bash
ncdu
```

## Test de vitesse d'écriture et lecture d'un disque
```bash
#!/bin/bash
echo -e "\n Vitesse d'écriture"
sync; dd if=/dev/zero of=/tmp/smart bs=1M count=1024; sync

echo -e "\n Vitesse de lecture"
dd if=/tmp/smart of=/dev/null bs=1M count=1024

rm -rf /tmp/smart
```

## Afficher le type de disque, HDD, SSD...
```Bash
sudo fdisk -l /dev/sda | grep -m1 ^Disk | awk '{print $3 " " $4}'
```
Ou
```Bash
cat /sys/class/block/sda/device/model
```

## Activer TRIM pour optimiser les performances d'un SSD
```Bash
sudo systemctl enable fstrim.timer
```

## Réparation d’un disque dur, avec certains secteurs endommagés
* Attention le test ne doit pas être fait sur un disque monté, il faut donc utiliser un live cd.

1. La première étape consiste à identifier le disque.
```Bash
lsblk
```
Ou
```Bash
fdisk -l
```

2. Utiliser la commande badblocks pour rechercher des secteurs défectueux
   * Soit en écriture
```Bash
badblocks -wvs /dev/sdx 
```

   * Soit en lecture
```Bash
badblocks -nvs /dev/sdx
```

3. Si nous trouvons des secteurs défectueux on va les enregistrer dans un fichier
```Bash
badblocks -wvs /dev/sdx > badblocks.txt
```

4. Utiliser la commande fsck ou e2fsck pour tenter de réparer les secteurs défectueux
```Bash
e2fsck -cfpv /dev/sdx  < badblocks.txt
```

* Avec la commande fsck
```Bash
sudo fsck -C -t ext4 -l badblocks.txt /dev/sdxx
```

### Autre solution avec la commande e2fsck
* Comprend badblocks, avec un test de lecture et écriture.
```Bash
e2fsck -ccDFY /dev/sdX
```
* Peut prendre plusieurs jour, selon les ressources de votre ordinateur.

## Afficher le statut d'une configuration RAID logiciel
```Bash
cat /proc/mdstat
```

## Afficher le nom des disques ou le type
```Bash
lsblk -ldn -I 8 -o NAME

sda
```

```Bash
lsblk -ldn -I 8 -o SIZE,MODEL

447,1G SanDisk SSD PLUS 480 GB
```

## Formater un disque
Nettoyage du disque et création d'une nouvelle table de partitions GPT.
```Bash
wipefs --all /dev/sdX

sgdisk --zap-all /dev/sdX
sgdisk --clear /dev/sdX
sgdisk --verify /dev/sdX
```

Création d'une nouvelle partition.
```Bash
sgdisk --largest-new=1 /dev/sdX
```

Formatage de la partition en FAT32
```Bash
mkfs.fat -F32 /dev/sdX1
```

## Afficher les statistiques sur les entrée, sortie des disques
|Option|Description|
|---|---|
|-x|Pour afficher les statistiques étendues.|
|-N|Affiche les statiques d'un disque donné.|

```Bash
iostat -Nx sda
```

## Changer les disques d'une machine vers une autre
En root effacer le fichier /etc/udev/rules.d/70-persistent-net.rules.
Redémarrer la machine.
Il y aura le problème LSB interface c'est normale car c'est la régénérescence du nouveau fichier "/etc/udev/rules.d/70-persistent-net.rules" mit à jour!.

## FSCK
Permet de réparer ou vérifier le système de fichiers,
ne peut se faire que sur des périphériques non montés.

Lancement du test
```Bash
fsck /dev/sda
```

-f pour forcer le teste
-c pour vérifier les secteurs défectueux

Vérifier tous les montages fait avec fstab
```Bash
fsck -AR -y /dev/sda
```

## Clonage d'un disque vers un autre en direct

Sur le pc cible démarrer un livecd
Sur le pc source démarrer aussi un live cd

Utiliser la commande cat ou pv et dd pour faire le clonage
Cat ou pv est plus rapide que dd

```Bash
pv /dev/sda | ssh 192.168.1.54 'cat > /dev/sdb'
```

Faire un sync sur les deux machines à la fin
```Bash
sync
```

## Afficher les devices montés
```Bash
cat /etc/mtab
```
ou
```Bash
cat /proc/mounts
```

## Accès sur un seul disque qui était en raid 1 pour récupérer des données
```Bash
apt-get install mdadm
```

Démonter le raid
```Bash
umount /dev/md0
```

## Récupération de données d’un RAID5
Utilisation d'un live cd debian https://cdimage.debian.org/mirror/cdimage/archive/8.11.0-live/amd64/iso-hybrid/
Réassemblage du raid logiciel dans un système livecd

Installation de MDADM
```Bash
apt install mdadm
lsblk
```

Création du raid
```Bash
mdadm --create /dev/md2 --level=5 --raid-device=3 /dev/sd[a-b-c]4
```

Vérification du montage
```Bash
cat /proc/mdstat
lsblk
```

## Réassemblage d'un raid logiciel
Exemple:
```Bash
mdadm --create /dev/md0 --level=5 --raid-device=3 /dev/sd[a-b-c]2
mdadm --create /dev/md1 --level=5 --raid-device=3 /dev/sd[a-b-c]3
mdadm --create /dev/md2 --level=5 --raid-device=3 /dev/sd[a-b-c]4
cat /proc/mdstat
lsblk
```

```Bash
tune2fs -O ^metadata_csum /dev/sdb1
```
## Réparer une clé usb
```Bash
lsblk
sudo fsck /dev/sdc1
```

## Tester les secteurs morts d’un disque dur
J'ai utilisé e2fsk, qui comprend des badblocks, avec un test de lecture écriture.
```Bash
e2fsck -ccDFY /dev/sd…
```
