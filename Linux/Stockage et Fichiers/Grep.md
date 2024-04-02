## Supprimer des lignes spécifiques d'un fichier
Utiliser grep
```Bash
grep -v 'motiv' file
```
-v exclure les lignes qui correspondent

Supprimer toutes les lignes contenant le mot "erreur"
```Bash
grep -v 'erreur' exemple.txt
```

Modifier le fichier d'origine
```Bash
grep -v 'erreur' sample.txt > temp.txt && mv temp.txt sample.txt
```

## Supprimer des lignes correspondant à plusieurs motifs
```Bash
grep -v -E 'erreur|avertissement' nom de fichier
```
