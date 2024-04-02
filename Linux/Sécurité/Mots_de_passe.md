## Mot de passe root perdu
* Récupérer une machine bloquée car on a perdu les identifiants.
1. Au moment de l'affichage du menu grub
appuyer sur "e"
2. chercher la ligne qui commence par "linux", et à la fin de cette ligne saisir "init=/bin/bash" remplacer aussi "ro" par "rw" si besoin.
3. Taper F10 pour valider.
* On se retrouve dans une console en tant que root, on peut faire `passwd root` pour changer le mot de passe root.

## Génération de mots de passe aléatoires
```bash
tr -dc [:upper:][:lower:][:digit:][:punct:] < /dev/urandom | head -c12 && echo
```
