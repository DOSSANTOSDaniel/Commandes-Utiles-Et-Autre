## La commande netcat
```bash
nc -zv localhost 22
```

## Partager un fichier au travers d'internet sur le port 8000
* Sur la machine A.
```Bash
nc -v -l 8000 < fichier.txt
```

* Sur la machine B
```Bash
nc 192.168.1.42 8000
```

## Afficher le résultat d'une commande sur un navigateur web ou terminal
```Bash
while true; do timeout 1 nc -w 1 -l 8844 <<< $(hostnamectl); done
```

```Bash
nc 127.0.0.1 8844
```
* Consulter aussi http://127.0.0.1:8844/

## La commande netcat
```Bash
netcat [OPTIONS] [HOST:[PORT]
```

Pour créer une connexion à un hôte
```Bash
netcat ip port
```

Ecouter sur un port particulier
```Bash
nc -l -p 12345
```

Connexion à ce port
```Bash
nc ip 12345
```

Par défaut il utilise TCP

pour utiliser UDP
```Bash
nc -u ip port
```

Transfert de fichiers
machine target
```Bash
nc -l -p 12345 > file.txt
```

Machine qui envoie les données
```Bash
netcat ip 12345 < file.txt
```

Identifier un service sur un port donné
```Bash
echo "" | nc ip port

echo "" | nc 192.168.1.22 22
```

Analise des ports comme nmap
```Bash
nc -z ip (port range)
```

Pour voir si le port 80 est en écoute sur le serveur
```Bash
nc -vz 192.168.0.30 80
```

## Partager un fichier au travers d'internet sur le port 8000
* Sur la machine A.
```Bash
nc -v -l 8000 < fichier.txt
```

* Sur la machine B
```Bash
nc 192.168.1.42 8000
```
