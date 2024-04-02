# Docker

## Supprimer toutes les images et containers d'un coup sur Docker
```bash
docker system prune
```

## Partager le volume d'un conteneur(Docker)
```Bash
docker run -d  -p 443:443 -v dokuwiki:/var/www/html:z daniel
```
L'option «z» indique à Docker que le contenu du volume sera partagé entre les conteneurs.
Docker étiquettera le contenu avec une étiquette de contenu partagé.
Les étiquettes de volumes partagés permettent à tous les conteneurs de lire / écrire du contenu.
suite à cela on pourra écrire directement sur /var/lib/docker/volume...

## Troubleshoot sur conteneur docker
Comment afficher les logs d'un conteneur
```bash
docker logs "name or id"
```

Pour voir les logs en temps réel
```bash
docker logs -f "name or id"
```

Pour voir les logs avec les timestanps
```bash
docker logs -t "name or id"
```

Rechercher des logs depuis un certain horodatage, exemple depuis 30 minutes
```bash
docker logs --since 30m "name or id"
```

Rechercher des logs avant un certain horodatage, ici 30 minutes
```bash
docker logs --until 2023-08-27T18:30:00.893455245Z "name or id"
```

Afficher les erreurs
```bash
docker logs nginx | grep "failed"
```

Utiliser journalctl
```bash
sudo journalctl -u docker.service
```
