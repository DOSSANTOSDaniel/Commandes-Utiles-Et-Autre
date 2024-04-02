## Afficher l'UID de l'utilisateur courant
```bash
cat /proc/self/loginuid
```

## Afficher des information sur un utilisateur

### Avec la commande `pinky`
```bash
pinky -l daniel

Identifiant : daniel                      Nom réel :  daniel
Répertoire : /home/daniel                 Interpréteur :  /bin/bash
```

## Afficher le nombre maximal et le minimal de comptes utilisateurs possibles 
```Bash
grep -E '^UID_MIN|^UID_MAX' /etc/login.defs

UID_MIN			 1000
UID_MAX			60000
``` 

## Afficher les comptes utilisateurs
```Bash
getent passwd {1000..60000}
``` 

## Afficher le UID,GUID et autres groupes associés à l'utilisateur courant
```bash
id daniel

uid=1000(daniel) gid=1000(daniel) groupes=1000(daniel),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),108(kvm),121(lpadmin),131(lxd),132(sambashare),134(libvirt),136(docker)
```

## Affiche le nom de l'utilisateur courant
```Bash
id -un
```

### Savoir quand un système a été redémarré ou arrêté pour la dernière fois
```Bash
sudo last -1 reboot
sudo last -1 shutdown
```

### Savoir qui est connecté au système
```Bash
w
who
users
```

## Fermer une session appartenant à un certain utilisateur
```Bash
loginctl kill-user daniel
```

## Obtenir le numéro d'identifiant de l'utilisateur courant
```Bash
echo $EUID
```

## Surveillance des utilisateurs sur linux
Afficher les connexions précédentes
```Bash
last
```

Utilisateurs actuellement connectés
```Bash
last | grep "logged in"
```
ou
```Bash
w
```

Infos de connexion de tous les utilisateurs
```Bash
sudo lastlog
cat /var/log/auth.log
sudo grep "Failed" /var/log/auth.log
```
