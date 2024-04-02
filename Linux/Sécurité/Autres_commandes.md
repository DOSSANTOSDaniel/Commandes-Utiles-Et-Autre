# Autres commandes

## Générer un hash MD5 d'une chaîne de caractères
```Bash
md5sum <<<"test"
```

## Rendre nos commandes invisibles à l'historique des commandes
```Bash
nano ~/.bashrc
```

```Bash
export HISTCONTROL=ignorespace
```

Puis écrire les commandes toujours avec un espace devant.

## Désactiver le compte root
```bash
passwd -l root
```
Ou
```bash
passwd --lock root
```