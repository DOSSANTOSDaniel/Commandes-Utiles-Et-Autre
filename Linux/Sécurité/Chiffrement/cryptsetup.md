## Chiffrement d'une partition
Création de la partition de travail chiffrée et définition du mot de passe.
```Bash
cryptsetup luksFormat /dev/sdX1
```
 
Déverrouillage de la partition avec le mot de passe créé précédement.
```Bash
cryptsetup open /dev/sdX3 cryptroot
```