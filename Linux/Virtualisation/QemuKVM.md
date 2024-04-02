# Qemu/KVM/Proxmox

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
sudo apt install sudo spice-vdagent spice-webdavd qemu-guest-agent git vim -y
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

visudo
#Décomenter cette ligne
%wheel ALL=(ALL:ALL) ALL

pw groupmod wheel -m MY_USER
reboot

sudo service qemu-guest-agent enable
sudo service qemu-guest-agent start
```