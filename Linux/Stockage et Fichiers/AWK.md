## Afficher la première et la dernière ligne d'un fichier avec awk
```Bash
awk 'NR==1{print} END{print}'
```

### Exemple
```Bash
df -h --total | awk 'NR==1{print} END{print}'

Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
total              449G    255G  172G  60% -
```

## Supprimer des lignes spécifiques d'un fichier
Utiliser awk
```Bash
awk 'NR!=nb ligne' file
```
NR : nombre d'enregistrement = numéro de ligne

Supprimer la 3eme ligne
```Bash
awk 'NR!=3' exemple.txt
```

Modifier le fichier d'origine
```Bash
awk 'NR!=3' sample.txt > temp.txt && mv temp.txt sample.txt
```
