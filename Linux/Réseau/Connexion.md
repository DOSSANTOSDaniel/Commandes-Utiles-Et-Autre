## Connexion à une machine linux sans écran ni clavier (à tester)
```Bash
apt-get install udhcpd

nano -c /etc/default/udhcpd
```

ligne 2

```
DHCPD_ENABLED="no"  >>>  DHCPD_ENABLED="yes"
```

```Bash
nano -c /etc/udhcpd.conf

/etc/init.d/udhcpd start

grep udhcpd /var/log/syslog
```

## Connecter un pc à un autre via un câble Ethernet

Sur le PC maître, fixer l'adresse IP
```Bash
vim /etc/network/interfaces

---
iface ens18 inet static
        address 10.10.0.5/24
        network 10.10.0.0
        broadcast 10.10.0.255
---
```

Installation du serveur dhcp :
```Bash
apt install isc-dhcp-server -y

vim /etc/dhcp/dhcpd.conf
---
1
---
```

Indiquer l'interface :
```Bash
vim /etc/default/isc-dhcp-server
---
2
---

systemctl start isc-dhcp-server.service
```

Si problèmes
```Bash
jourmalctl -u isc-dhcp-server
```

## Récupération de l'adresse IP du deuxième poste
```Bash
dhcp-lease-list
```