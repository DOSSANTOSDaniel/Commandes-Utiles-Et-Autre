# Proxmox

## Créer ou ajouter un cluster sur Proxmox
Création du cluster.
```Bash
pvecm create CLUSTERNAME
```

Ajouter un nœud sur le cluster.
```Bash
pvecm add IP-ADDRESS-CLUSTER
```

## Enlever la bannière de souscription sur Proxmox 
```Bash
cd /usr/share/javascript/proxmox-widget-toolkit
```

Faire une sauvegarde du fichier de configuration.
```Bash
cp proxmoxlib.js proxmoxlib.js.save
```

Éditer le fichier.
```Bash
nano proxmoxlib.js
```

* Rechercher l'occurrence "if (data.status !== 'Active') {"
et là remplacer par "if (false) {".

Redémarrer le service proxmox, ne pas oublier de vider le cache des navigateurs web.
```Bash
systemctl restart pveproxy.service
```

## Préparation des machines virtuelles sur Qemu/KVM/Proxmox

### Configuration des conteneurs

#### Configuration de l'heure
```Bash
sudo ln -fs /usr/share/zoneinfo/Europe/Paris /etc/localtime
```
### Configuration des VM's

#### Debian
```Bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install sudo spice-vdagent spice-webdavd qemu-guest-agent acpid git vim -y
#systemctl start qemu-guest-agent && systemctl status qemu-guest-agent
usermod -a -G sudo daniel
reboot
```

#### Ubuntu
```Bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install sudo spice-vdagent spice-webdavd qemu-guest-agent git vim -y
```

#### Fedora
```Bash
sudo dnf upgrade --refresh --assumeyes
sudo dnf install spice-vdagent spice-webdavd qemu-guest-agent git vim --assumeyes
```

#### ArchLinux
```Bash
sudo pacman -Suyy
sudo pacman -S spice-vdagent qemu-guest-agent git vim
#sudo pacman -S qemu-block-gluster
#sudo pacman -S qemu-block-iscsi
```

#### OpenSUSE
```
Activer QEMU guest agent dans la configuration de la VM

sudo zypper refresh
sudo zypper update

sudo zypper install qemu-guest-agent
sudo systemctl enable qemu-guest-agent

#sudo zypper install spice-vdagent
#systemctl --user enable spice-vdagent.service

sudo reboot
```

#### FreeBSD
```Bash
su -
freebsd-update fetch
freebsd-update install
pkg update
pkg upgrade

pkg install sudo qemu-guest-agent git vim
# pkg install spice-protocol

visudo
#Décomenter cette ligne
%wheel ALL=(ALL:ALL) ALL

pw groupmod wheel -m MY_USER
reboot

sudo service qemu-guest-agent enable
sudo service qemu-guest-agent start

# echo "qemu_guest_agent_enable="YES"" >> /etc/rc.conf
# echo "qemu_guest_agent_flags="-d -l /var/log/qemu-ga.log"" >> /etc/rc.conf
# service qemu-guest-agent start
```

#### Windows

[spice-guest-tools](https://www.spice-space.org/download/windows/spice-guest-tools)
[spice-webdavd](https://www.spice-space.org/download/windows/spice-webdavd)

Pour l'invité Windows, en plus d'installer spice-guest-tools, je devais faire ce qui suit dans virt-manager:
Ajouter du matériel -> Canal, définir le nom sur "com.redhat.spice.0" (ou similaire), définir l'appareil tapez "Agent d'épices (spicevmc)".
J'ai trouvé ces informations dans ce post reddit après une longue recherche: reddit.com/r/linux/comments/asw4wk

## Commandes de l'agent qemu
* Commande pour l'aide `qemu-ga -h`.

## Commandes sur Proxmox

### Afficher les performances
```bash
pveperf
```

### l’emplacement des templates
```bash
pveam list local
```

### mise à jour du serveur Proxmox
```bash
pveam update
```
 
### liste des stockages en zfs
```bash
zfs list
```

### Qemu agent
```bash
qm agent <vmid> ping
qm set VMID --agent 1
```

Utiliser l'agent qemu
```bash
./qemu-ga -h
```

Lister les vms
```bash
qm list
```

Joindre un node au cluster via ssh
```bash
pvecm add IP-ADDRESS-CLUSTER
```

Etat du cluster
```bash
pvecm status
```

Lister tous les nodes
```bash
pvecm nodes
```

Supprimer un node du cluster
```bash
pvecm delnode pve4
Killing node 4
```

Information stockage 
```bash
cat /etc/pve/storage.cfg
```

Lister les images
```bash
pvesm list IsoImages
pvesm list local
```