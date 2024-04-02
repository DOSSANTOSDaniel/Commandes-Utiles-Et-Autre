## Vérifier les dépendances d’un paquet sur Ubuntu et Debian
```Bash
apt-cache depends vlc
```

## Liste des paquets orphelins "deborphan"

### Supprimer les paquets orphelins
```Bash
sudo apt-get purge $(deborphan)
```
Ou
```bash
sudo apt-get remove --purge $(deborphan)
```

## Commandes permetant de savoir si une commande est installée
```bash
apt list --installed | grep <package-name>
dpkg -l | grep <package-name>
yum list installed | grep <package-name>
dnf list installed | grep <package-name>
rpm -qa | grep <package-name>
pacman -Q | grep <package-name>
zypper search --installed-only <package-name>
```
