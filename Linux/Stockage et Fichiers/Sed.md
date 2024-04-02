## L'option -i."nom" de la commande sed permet de faire une sauvegarde avant de modifier le contenu d'un fichier
```Bash
sed -i.bak "s/loglevel=3 quiet/loglevel=4" /etc/default/grub
```

## Supprimer des lignes spécifiques d'un fichier
```Bash
sed 'patern ou nb ligne' file
```

Supprimer la 5eme ligne
```Bash
sed '5d' file
```

Supprimer plusieurs lignes
```Bash
sed -e '5d' -e '7d' exemple.txt
```

Supprimer une plage de lignes
```Bash
sed nom de fichier '3,5d'
```
