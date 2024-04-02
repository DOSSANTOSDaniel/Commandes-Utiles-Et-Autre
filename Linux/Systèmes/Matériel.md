## Enlever les bips système sur Debian
```Bash
sudo rmmod pcspkr
```
* Puis, éditez le fichier /etc/rc.local et ajoutez la commande précédente avant le "exit 0" afin que la commande soit conservée après le redémarrage du système.

## Afficher la résolution de l’écran
```Bash
xrandr -q | grep \*
```

## Mettre à jour le firmware de certains périphériques si possible.
```bash
apt update && sudo apt upgrade -y
service fwupd start
```

```Bash
fwupdmgr get-devices
```

```Bash
fwupdmgr refresh
```

```Bash
fwupdmgr get-updates
```

```Bash
fwupdmgr update
```

## Désactiver la luminosité sur un écran
```Bash
echo 0 > /sys/class/backlight/radeon_bl0/brightness
```

## Connaître la version de tpm
```bash
lsmod | grep tpm
```

## Température du processeur
```bash
sudo apt installer lm-sensors
sudo sensors-detect
sensors
```
