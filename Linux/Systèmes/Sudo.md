## Mise en place du sudo sur Debian
Sudo n’est pas installé par défaut sur Debian.
installation de sudo
```Bash
su -
apt install sudo
```

Editer le fichier de configuration de sudo
```Bash
visudo
```

Deux solutions pour donner les droits root à notre utilisateur, soit rajouté dans le fichier sudoers
```Bash
daniel ALL=(ALL:ALL) ALL
```

L’autre solution est d'ajouter l’utilisateur daniel au groupe sudo
```Bash
adduser daniel sudo
```
Ou
```Bash
usermod -aG sudo daniel
```

Ne pas oublier de redémarrer ! ou de se reloger !
