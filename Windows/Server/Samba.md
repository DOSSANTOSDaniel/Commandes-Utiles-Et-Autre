## Déconnecter un utilisateur samba sur windows
Windows par défaut conserve une connexion aux partages à chaque fois qu’on se connecte à une autre machine ou à un autre serveur.
Pour se déconnecter, il faut se déconnecter des partages de la machine distante.

Pour voir les connections en cours.
```
net use
```

Pour supprimer une connexion.
```
net use \\<machine>\<partage> /delete							
```