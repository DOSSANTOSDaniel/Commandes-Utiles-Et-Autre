## Visualiser et effacer les métadonnées d'un fichier
* Les fichiers que vous avez créé contiennent des données cachées.
* Mat (Metadata Anonymisation Toolkit) va nous permettre de visualiser les différentes traces
laissées sur nos fichiers.
* Il permet aussi d’effacer ces données pour rendre nos fichiers un peu
plus anonymes.

1. Installation de MAT.
```Bash
sudo apt-get install mat
```
|Commande|Description|
|---|---|
|`mat2 --list`|Liste les différents formats de fichiers supportés.|
|`mat2 --verbose`|Affiche des informations plus détaillées.|
|`mat2 --show`|Affiche les métadonnées d'un fichier.|
|`mat2 --help`|Afficher l’aide.|
|`mat2 --version`|Affiche la version du programme.|
|`mat2 --inplace`|Supprime les métadonnées.|

2. Afficher les métadonnées sans les supprimer.
```Bash
mat2 --show IMG_20200305_175904.jpg
```
3. Anonymisation des données.
* Supprime les métadonnées associées au fichier.
```Bash
mat2 --verbose --inplace IMG_20200305_175904.jpg
```
