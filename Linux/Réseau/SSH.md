## Éditer un fichier au travers d'internet

### Avec la commande ssh
```Bash
ssh -p 2244 daniel@192.168.1.85 -t sed -i 's/Bonjour/Bonsoir/g' /home/daniel/exemple.txt
```

## Lancer une application graphique d'une machine distante sur une machine locale
```Bash
ssh -X -t daniel@192.168.1.40 'firefox'
```

## Maintenir la connexion SSH
```bash
ssh -o "ServerAliveInterval 60" user@domain
```

## Effacer un host ssh
```Bash
ssh-keygen -R 192.168.1.22

WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
ssh-keygen -R "le srv"

exemple:
ssh-keygen -R 192.168.0.90
```

## Ajouter une bannière à la connexion SSH
Création et édition du fichier sshd-banner.
```Bash
sudo vim /etc/ssh/sshd-banner
```

Configuration de la bannière dans le fichier de configuration de SSH, placer cette ligne dedans
"Banner /etc/ssh/sshd-banner".
```Bash
sudo vim /etc/sshd/sshd_config
```

```Bash
sudo systemctl restart sshd
```

## Lancer des applications distantes,(graphiquement) via SSH
X Forwarding

1. Modifier le fichier /etc/ssh/sshd_config.
```Bash
X11Forwarding yes
```

2. Lancer une application qui est installée sur la machine distante et avoir l'affichage sur la machine locale.
```Bash
ssh -XC daniel@192.168.1.22 gedit
```

Pour lancer une application installée sur la machine distante avec un affichage sur la machine distante.
```Bash
ssh -XC daniel@192.168.1.22 export DISPLAY=:0.0 gedit
```

La variable DISPLAY permet de d'afficher le numéro d'affichage de l'écran principal.
```Bash
echo $DISPLAY
```

## Connexion SSH en mode non interactif avec mot de passe
```Bash
apt install sshpass

sshpass -P <mot de passe> ssh daniel@192.168.1.22 "ls -l"
```

## Montage d'un dossier ou d'un système de fichiers au travers de SSH
Sur la Machine locale
```Bash
mkdir /home/daniel/remote_host_ananas
sshfs ananas@192.168.1.42:/home/ananas /home/daniel/remote_host_ananas -o idmap=user -o reconnect -o sshfs_sync
```

### Vérification du montage
```Bash
ps -aux | grep sshfs
findmnt | grep remote_host_ananas
mount | grep remote_host_ananas
```

### Pour démonter le montage
```Bash
fusermount -u /home/daniel/remote_host_ananas
```

## Sauvegarde d'un périphérique dans un fichier sur un poste distant via SSH
```Bash
dd if=/dev/sda | ssh daniel@192.168.1.22 'dd of=sda.img'
```

## Déconnecter une session SSH
```Bash
who -a
```

```Bash
w
```

```Bash
ps ax | grep pts/0
```

```Bash
kill -9 3227
```
Chaque utilisateur a un pts/x (Terminal virtuel)

## Maintenir une connexion ssh
```Bash
ssh -o "ServerAliveInterval 60" user@domain
```

## Compresser et décompresser avec tar via ssh
```Bash
tar czf - "~/Documents/myfolder" | ssh ramces@remote.host "tar xzf - -C ~/Documents/"
```

```Bash
ssh ramces@remote.host "tar czf - ~/Documents/myfolder" | tar xzf - -C "~/Documents/"
```

## Transmettre un fichier via ssh
```Bash
cat < my.local.file | ssh ramces@remote.host "cat > my.remote.file"
```

```Bash
ssh ramces@remote.host "cat < my.remote.file" | cat > my.local.file
```

## Sauvegarde et restauration de disque via ssh
```Bash
sudo dd if=/dev/sda | ssh ramces@remote.host "dd of=sda.img"
```
```Bash
ssh ramces@remote.host "dd if=sda.img" | sudo dd of=/dev/sda
```
```Bash
sudo dd if=/dev/sda4 | ssh ramces@remote.host "dd of=home.img"
```

## Impression de texte sur une console distante
Sur la machine A
```Bash
mkfifo my-fifo
tail -f my-fifo | ssh root@remote "cat > /dev/tty1"
echo "Hello, MakeTechEasier!" > my-fifo
```

Sur la machine B
savoir quelle console utiliser
```Bash
who -a
```

## Impression de texte sur une console virtuelle distante
Sur la machine A
```Bash
mkfifo my-fifo
tail -f my-fifo | ssh root@remote "cat > /dev/pts/1"
echo "Hello, MakeTechEasier!" > my-fifo
```

Sur la machine B
```Bash
tty
```