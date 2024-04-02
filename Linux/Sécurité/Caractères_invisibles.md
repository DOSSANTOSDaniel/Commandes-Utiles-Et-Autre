## Afficher les caractères invisibles
```Bash
cat -A script.sh
```

### Exemple sur un document à la ligne 197
```Bash
cat -A script.sh | sed -n 197p 
```