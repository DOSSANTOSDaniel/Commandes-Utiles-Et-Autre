# Maintenance

## Récupérer une partition corrompue
Vérifie et tente de réparer les erreurs sur le disque.
```
CHKDSK /R
```

## Nettoyer Winsys
Le dossier WinSxS contient des fichiers en rapport avec l’utilisation de Windows Update et
l'installation de nouvelles versions de composants.

Analyser la taille réelle du dossier WinSxS, ouvrir le terminal
Powershell en administrateur et tapez:
```Powershell
Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
```

Nettoyage avec la commande StartComponentCleanup si recommandé
```Powershell
Dism.exe /Online /Cleanup-Image /StartComponentCleanup /resetbase
```
Cette commande va permettre la suppression de paquets inutiles et aussi de compresser
certains composants pour gagner de l’espace.
L’option "/resetbase" permet de supprimer toutes les versions obsolètes des différents
composants.

