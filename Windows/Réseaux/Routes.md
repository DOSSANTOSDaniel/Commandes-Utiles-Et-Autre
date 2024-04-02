## Ajouter une route

Afficher la table de routage
```Cmd
route print
```
route PRINT -4 : ipv4
route PRINT -6 : ipv6

Ajouter une route statique sans persistance
```Cmd
route add 0.0.0.0 mask 0.0.0.0 192.168.1.1
```

Ajouter une route statique avec persistance
```
route -p add 0.0.0.0 mask 0.0.0.0 192.168.1.1
   	^  ^ 	^        	^     	^
   	|  | 	|        	|     	|     	 
  Persistence   |        	|     	|     	 
      	| 	|    	mask cible	|	 
    	Ajout   |                  	| 	 
            	|              	passerelle connectée au réseau cible
       	Cible réseau      	 
```

Supprimer une route
```Cmd
route delete 10.0.0.0 mask 255.255.255.0
```

Supprimer toutes les routes
```Cmd
route -f
```

