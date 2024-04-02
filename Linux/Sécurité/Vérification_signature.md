## Vérification de la signature d'un fichier
```Bash
sha1_sig='9ab59cddf97e52762039431d60567d6d69979f5f' ; check_sha1="$(sha1sum debian.iso | awk '{print $1}')" ; [[ $check_sha1 == $sha1_sig ]] && echo 'Signature valide' || echo 'Erreur de signature'
```
