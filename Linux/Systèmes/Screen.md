## Utilisation de la commande `screen`

### Créer un screen
```Bash
screen -S "nom"
```

### Se détacher du screen
* `Ctrl a + d`

### Se rattacher au screen 
```Bash
screen -r "nom"
```

### Lister les screens ouverts
```Bash
screen -ls
```

### Fermer un screen 
```Bash
exit
```

### Se connecter à un screen non détaché 
```Bash
screen -x "nom"
```
