# VirtualBox

## Se connecter via ssh sur une machine derrière un réseau NAT sur VirtualBox
Pour créer une règle de transfert de port pour la machine virtuelle invitée nommée "Centos",
avec l'adresse IP 10.0.2.15 et le port SSH 22, mappé à l'hôte local sur le port 2522

Eteindre la vm

### Lister les machines virtuelles
```Bash
vboxmanage list vms
```

### Création d'une règle de port forwarding sur le port 22
* Adresse IP de la machine virtuelle : 10.0.2.15
* Port en écoute sur cette machine virtuelle : 22
```bash
vboxmanage modifyvm "Debian" --natpf1 "SSH,tcp,127.0.0.1,2222,10.0.2.15,22"
```

### Vérification
```Bash
vboxmanage showvminfo "Debian" | grep SSH
```

### Connexion à la machine virtuelle à partir de la machine hôte
```Bash
ssh -p 2222 daniel@127.0.0.1
```

## Convertir un disque vdi au format vmdk
```Bash
vboxmanage internalcommands converttoraw debian.vdi debian.raw
```

```Bash
qemu-img convert -O vmdk debian.raw debian.vmdk
```

```Bash
rm debian.raw
```

## Amorçage d’un disque dur physique ou clé USB sur VirtualBox 
* Cette méthode est appelé  VirtualBox "raw hard disk access."
* Créer une configuration de machine virtuelle, puis au moment de créer le disque virtuel cocher : “ne pas ajouter de disque dur virtuel” puis valider.

Brancher votre disque dur ou clé USB sur l’ordinateur et identifier le support.
```Bash
lsblk
```

Une fois le support identifié, il faut identifier le groupe qui a les droits sur les supports.
```Bash
ls -la /dev/sdX
```

Il faut ajouter l’utilisateur courant au groupe trouvé précédemment. 
```Bash
usermod -a -G <groupe> <utilisateur>
```

Attention pour que cela prenne effet il faut se reconnecter sur sa session ou taper la commande `newgrp`.

Se rendre dans le dossier de VirtualBox.
```Bash
cd /home/<utilisateur>/VirtualBox VMs
```

Création du lien entre un disque physique vers un disque logique.
```Bash
VBoxManage internalcommands createrawvmdk -filename <nom du nouveau disque>.vmdk -rawdisk /dev/sdx -partitions <numéro de partition>
```

Configuration des droits.
```Bash
chown <utilisateur>:<utilisateur> <nom du nouveau disque>.vmdk
```
Allez dans les configuration de la machine virtuelle précédemment créé à l’onglet stockage puis sélectionnez ajouter un disque existant et choisissez le disque vmdk que nous avons créé.
Pour finir démarrer la machine virtuelle.

## Augmenter la taille d’un disque virtuel sur VirtualBox
Sur la machine physique
```Bash
vboxmanage controlvm debian poweroff
```

```Bash
vboxmanage modifymedium /home/daniel/VirtualBox\ VMs/debian/debian-disk.vdi --resize 5500000
```
* La taille doit être exprimée en mégaoctets.

```Bash
vboxmanage startvm debian --type headless
```

```Bash
ssh daniel@192.168.1.22
```

Sur la machine virtuelle.
```Bash
screen -S resize_vm
```

```Bash
df -h
```

```Bash
resize2fs /dev/sda
```

Afficher l’évolution de l’agrandissement sur la machine virtuelle.
```Bash
whatch -n 1 -d df -h	
```

Désactiver le Swap.
```Bash
swapoff /dev/sda5	
```

Tue tous les processus qui utilisent la partition.
```Bash
fuser -k /dev/sd4	
```

## Mise en place d'un partage de fichiers sur VirtualBox
Sur la machine virtuelle, pour ajouter le groupe supplémentaire.
```Bash
usermod -a -G vboxsf <nom_utilisateur>
```

```Bash
 sudo mount -t vboxsf PartageVBox /media/sf_PartageVBox
```
Je peux voir mon dossier partagé qui est correctement monté et je peux y accéder.
Je peux même le remettre en montage automatique dans les paramètres de VirtualBox et ça marche toujours,
dès le démarrage de ma machine virtuelle, il apparaît comme étant monté et je peux y accéder.

## Connecter un périphérique USB sur une machine virtuelle avec Virtualbox
```bash
sudo usermod -aG vboxusers $USER
sudo reboot
```

## Convertir un disque en VDI
```bash
apt-get install qemu-utils
qemu-img convert -O vdi /dev/sdc /home/daniel/Mon_PC.vdi
```

## Exporter une VM virtualbox vers d'autres machines
Il y a deux méthodes :

1. on peut copier les fichiers de la vm puis là charger dans virtualbox à l'aide d'une commande
2. on peut exporter la vm

Methode par la copie de fichiers et du fichier .vbox
le fichier .vbox contient toutes les informations concernant la vm
on a besoin de copier le fichier de la vm plus le fichier .vbox correpondant

Sur le poste cible
Le dossier de la vm doit être envoyer sur le dossier des vm sur le poste cible
machines > add et choisir le fichier .vbox ou si non un double click sur .vbox

On peut faire l'enregistrement en ligne de commande
```bash
vboxmanage registervm ma_vm/.vbox
```

Méthode par exportation de la vm
file > export appliance
choisir le format Open Virtualization Format 1.0 il est le plus compatibles avec les autres versions
ça crée un fichier compressé OVF

Sur la machine cible il sufit de l'importer