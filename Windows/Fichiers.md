# Fichier

## Créer un fichier compressé ou mètre à jour un fichier compressé
```Powershell
Compress-Archive -Path .\toto.iso -Update -DestinationPath .\Exemple.zip
```

## Déplacer un fichier
```Powershell
Move-Item -Path .\toto.txt -Destination .\os\linux.txt
```

## Créer un fichier d’une taille spécifique, en octets
```Powershell
fsutil file createnew file.txt 5000
```

## Commandes windows stockage
Réparer les fichiers corrompues
```Powershell
sfc -scannow
```

Erreurs des disques durs, optimisations des données
```Powershell
chkdsk
```

