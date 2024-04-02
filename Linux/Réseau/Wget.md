## Afficher l’IP publique en ligne de commande

Avec wget
```Bash
wget -qO- http://ipv4.icanhazip.com/
```

```Bash
wget -qO- icanhazip.com
```

## Utilisation de wget

Téléchargement simple
```Bash
wger url
```

Pour spécifier le dossier de téléchargement
```Bash
wget -P dossier_de_téléchargement http://ftp.crifo.org/debian-cd/current/amd64/iso-cd/debian-11.5.0-amd64-netinst.iso
```

Pour spécifier le nom du fichier de sortie
```Bash
wget -O debian.iso http://ftp.crifo.org/debian-cd/current/amd64/iso-cd/debian-11.5.0-amd64-netinst.iso
```

Reprendre un téléchargement interrompu
```Bash
wget -c http://ftp.crifo.org/debian-cd/current/amd64/iso-cd/debian-11.5.0-amd64-netinst.iso
```

Limiter le débit
```Bash
wget --limit-rate 300K http://ftp.crifo.org/debian-cd/current/amd64/iso-cd/debian-11.5.0-amd64-netinst.iso
```
* Limitation de 300KB par secondes.

Téléchargement en tache de fond
```Bash
wget -b http://ftp.crifo.org/debian-cd/current/amd64/iso-cd/debian-11.5.0-amd64-netinst.iso
```
* Pour voire l'avancement consulter wget-log.

Téléchargement de plusieurs fichiers
```Bash
wget -i liste.txt
```

Télécharger un site web entier(récursivement)
```Bash
wget --recursive --no-clobber --no-parent url
```

Faire plusieurs tentatives pour les connexions lentes
```Bash
wget --tries=10 url
```

Mode silencieux
```Bash
wget -q url
```

Téléchargements avec authentifications
```Bash
wget --user=nom --password=pass url
```
ou
```Bash
wget --user=nom --ask-password url
```

Ignorer les controles SSL
```Bash
wget --no-check-certificate url
```

Télécharger depuis ftp
```Bash
wget ftp://url
```