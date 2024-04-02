## La commande install
La commande associe la copie de fichiers (cp) et la création de dossiers (mkdir), ainsi que la gestion des accès (chmod, chown) et autres fonctionnalités utiles (comme les sauvegardes).
Syntaxe
```Bash
install source dest
```

```Bash
install -v -D -t ~/samples/ src/sample.txt
install: creating directory '~/samples'
'src/sample.txt' -> '~/samples/sample.txt'
```
