## Test d'ouverture d'un port

### Avec la commande telnet
```bash
telnet localhost 22
```

## Tester rapidement si un port est en écoute sur un serveur distant

Syntaxe:
telnet <IP> <Port>
Exemple avec le serveur 192.168.0.30

```bash
telnet 192.168.0.30 22
Trying 192.168.0.30...
Connected to 192.168.0.30.
Escape character is '^]'.
SSH-2.0-OpenSSH_7.4p1 Debian-10+deb9u6
^C
Connection closed by foreign host.
```
Ici on peut observer que sur le serveur le port 22 est en écoute