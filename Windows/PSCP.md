## Transfert de fichiers de Windows vers Linux avec la commande pscp
### Sur la machine sous Windows
1. Télécharger pscp.exe ici : https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
2. Afficher le dossier où Powershell recherche les fichiers exécutables
```Powershell
get-item env:PATH
```
3. Mettre le fichier pscp.exe dans ce dossier.

### Afficher la version installé
```Powershell
pscp –V
```

### Envoyer un fichier 
```Powershell
pscp fichier.txt daniel@192.168.1.42:/home/daniel/Documents
```
