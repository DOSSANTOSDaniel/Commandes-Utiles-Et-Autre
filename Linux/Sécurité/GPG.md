## Mot de passe sur un fichier
### Chiffrer un fichier
```Bash
gpg -c fichier
```

### Pour déchiffrer
```Bash
gpg fichier.gpg
```

### Utiliser un autre algorithme
```Bash
gpg -c --cipher-algo nom_algorithme fichier
```