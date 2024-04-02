## Gestion des paquets avec pkg (FreeBSD)
Il y a deux technologies complémentaires permettant l'installation de logiciels.

1. Les ports FreeBSD
Installation à partir des sources.
Le port freeBSD est un ensemble d'outils permettant l'automatisation du processus de compilation d'une application à partir de son code source!

2. Les paquets
Installation de binaires précompilés.
On manipule les paquets avec la commande pkg.

Savoir quelle version vous utilisez
```bash
freebsd-version
```

Version du noyau
```bash
uname -r
```

La commande `freebsd-update` est utilisée sur FreeBSD pour mettre à jour le système de base (le noyau et les bibliothèques système).
Cela concerne les correctifs de sécurité et les nouvelles versions de celui-ci.

Mise à jour de la base des correctifs
```bash
sudo freebsd-update fetch
```

Après avoir récupéré la base des correctifs, on peut les installer
```bash
freebsd-update install
```

Il est possible en cas de problème de revenir à l'état précédent via la commande
```bash
freebsd-update rollback
```

La commande pkg est l'outil de gestion des paquets standard sur FreeBSD, utilisé pour gérer les logiciels tiers installés sur le système à l'aide du système de gestion de paquets.

installation
```bash
pkg install htop
```

Supprimer un paquet
```bash
pkg delete htop
```

Si on souhaite désinstaller ensuite les paquets orphelins (dépendances qui ne servent plus), on utilisera
```bash
pkg autoremove
```

Mise à jour
```bash
pkg update
pkg upgrade paquet
```

Et pour mettre à jour tous les paquets
```bash
pkg upgrade
```

Rechercher un paquet
```bash
pkg search htop
pkg search -R htop-3.2.2_1
```

Informations sur un paquet
```bash
pkg info htop
```

Lister les paquets installés
```bash
pkg info -q
```

Effacer le cache local
```bash
pkg clean
```
