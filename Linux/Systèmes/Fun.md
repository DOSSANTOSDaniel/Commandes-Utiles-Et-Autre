
## Fork bomb
```Bash
:(){:|:&};:
```

## Regarder Star Wars via telnet
```Bash
telnet towel.blinkenlights.nl
```

## FAKE OS INSTALL
http://fakeupdate.net/




## Autres commandes
```bash
sl
hollywood
apt-get moo
sudo apt-get install figlet
sudo apt-get install xcowsay 
sudo apt-get install oneko
sudo apt-get install cmatrix
fortune
bb

apt-get install cowsay
cowsay coucou !

toilet -F gay -F border coucou
toilet -f mono12 -F metal coucou

telnet towel.blinkenlights.nl

figlet

yes

xeyes

sudo apt-get install aview
asciiview Tux.png -driver curses
 
espeak "Hello Linux"
 
sudo apt-get install xsnow
```

## Carte du monde en ligne de commande
```Bash
telnet mapscii.me
```

## Afficher la météo sur le terminal
```bash
curl wttr.in
```

### Affichage de l'aide
```bash
curl wttr.in/:help
```

### Météo en français dans la ville de Massy
```bash
curl fr.wttr.in/Massy
```

### Les phases de la lune actuellement en France
```bash
curl fr.wttr.in/moon@+France
```

### Avec options
```bash
curl fr.wttr.in/Massy?0QF
```
|Option|Description|
|---|---|
|0|Affiche seulement la météo de la journée en cours.|
|Q|Affichage minimal.|
|F|Ne pas afficher la phrase de publicité|

### Création d'une image au format png, cette image est le résultat de la météo à Massy
```bash
curl fr.wttr.in/Massy.png --output Massy.png
```

```bash
curl -O fr.wttr.in/Massy.png
```

### Image avec transparence
```bash
curl fr.wttr.in/Massy_transparency=50.png --output Massy.png
```
- Transparence de 0 à 255.