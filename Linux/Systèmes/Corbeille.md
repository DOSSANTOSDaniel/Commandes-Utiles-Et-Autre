## Mise en place d'un système de corbeille en ligne de commande

### La commande trash

#### Installation
```bash
apt install trash-cli
```

#### Mettre un fichier à la corbeille
```bash
trash-put <fichier>
```

#### Lister les fichiers dans la corbeille
```bash
trash-list
```

#### Restaurer les fichiers
```bash
trash-restore
```

#### Vider la corbeille
```bash
trash-empty
```

### La commande gio

#### Installation
* gio est déjà installée sur la plupart des distributions Linux.

#### Mettre un fichier à la corbeille
```bash
gio trash <fichier>
```

#### Lister les fichiers dans la corbeille
```bash
gio list trash://
```

#### Vider la corbeille
```bash
gio trash --empty
```
