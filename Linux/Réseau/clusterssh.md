
## Exécuter plusieurs commandes sur plusieurs machines en même temps
### Installation de l'application clusterssh
```Bash
sudo apt-get install clusterssh
```

### Configuration 
```Bash
vim /etc/clusters

groupe_1 = machine1 machine2
groupe_2 = machine3 machine4

all = groupe_1 groupe_2
```

### Connexion aux machines
```Bash
cssh -l <username> <clustername>
```