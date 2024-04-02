## Supprimer proprement un fichier avec la commande shred dans le but d'éviter une éventuelle récupération 
```bash
shred -fuvz -n 5 "fichier"
```

|Option|Description|
|---|---|
|-f|Change les permissions en écriture si nécessaire.|
|-u|Supprime le fichier après écrasement.|
|-v|Affiche la progression.|
|-z|Ajout de zéros après la suppression du fichier.|
|-n|Nombres de phases d'écrasement du fichier.|
 