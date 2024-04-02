## Vérifier l'ouverture d'un port
```Powershell
netstat -an
```
n : En numérique c'est plus rapide.

## Pour filtrer le port 22
```Powershell
netstat -an | findstr ':22'
```

