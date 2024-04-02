## La commande SS
Afficher les ports en écoute sur un poste
```Bash
ss -tulnp
ss -lptnu
```

Les ports en cours de connexion
```Bash
ss -ap
```

## infos sur les connexions
-a : Toutes les connexion fermées ou pas
-l : En écoute
-t : TCP
-u : UDP
-n : Affiche l'adresse IP, pas de résolution de nom
-r : Résolution des adresses IP et ports
-e : Informations détaillées sur les connexions

### Les ports
De 0 à 65535 : ports possibles.
De 0 à 1024  : ports connus, ne pas les utiliser.

