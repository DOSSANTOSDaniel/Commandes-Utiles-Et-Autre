## Afficher les interfaces réseau et leur adresse MAC
```Bash
ip -br -c link show

lo               UNKNOWN        00:00:00:00:00:00 <LOOPBACK,UP,LOWER_UP> 
enp8s0           UP             xx:xx:xx:xx:xx:xx <BROADCAST,MULTICAST,UP,LOWER_UP> 
virbr0           DOWN           52:54:00:70:a6:b5 <NO-CARRIER,BROADCAST,MULTICAST,UP>
virbr0-nic       DOWN           52:54:00:70:a6:b5 <BROADCAST,MULTICAST> 
```

## Activer le mode promiscuité
Afficher les interfaces.
```Bash
ip l
```

```Bash
ip link set enp1s0 promisc on
```

|Drapeaux|Description|
|---|---|
|BROADCAST:|Broadcast.|
|MULTICAST:|Multicast.|
|PROMISC:|Mode promiscuité.|
|R:|Indique que l’interface est démarré.|
|UP:|Indique que l’interface est initialisé.|


### Afficher la table ARP
```Bash
ip neighbour
```