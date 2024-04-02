## Afficher les derniers fichiers consultés, modifié ...

### Modifier les deux derniers jours
```Bash
find /home -type f -mtime 2
```

### Modifier il y à deux minutes
```Bash
find /home -type f -mmin 2
```

### Créé les deux derniers jours
```Bash
find /home -type f -ctime 2
```

### Dernier accès des 2 dernières minutes
```Bash
find /home -type f -amin 2
```

### Dernier accès il y a plus de deux jours
```Bash
find /home -type f -amin +2
```

### Combinaison
```Bash
find /home -type f -amin +2 and -ctime -6
```

## Supprimer les dossiers vides
```Bash
find /home/daniel/Images -type d -empty -delete
```

## Changer les permissions de plusieurs fichiers à la fois, de manière récursive.
```Bash
find /home/daniel -type f -exec chmod 644 {} \;
```

## Niveaux de profondeur dans la recherche de fichiers avec la commande find
```Bash
find MyFiles/ -mindegree 3 -maxdegree 3 -type f
find MyFiles/ -mindegree 3 -type f
find /path/to/directory/ -mindepth 3 -maxdepth 5 -name file
```

## Pour chaque fichier trouvé xarg lui applique une action c’est comme for
```Bash
sudo find / -name "*.jpg" -mtime -1 | xargs tar cvfP /home/daniel/log.tar
```
