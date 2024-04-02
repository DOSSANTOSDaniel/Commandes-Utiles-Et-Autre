## Outil facilitant l'installation de gestionnaires de bureau sur Linux
```bash
tasksel
```

## Ascii art

### Logo Linux sur le terminal
```bash
linuxlogo -L list
```

```bash
neofetch
```

## Optimisation de LibreOffice
1. Aller dans Outils → Options → Libre Office → Avancé, décochez la case "utiliser un environnement d’exécution Java".

2. Aller dans Outils → Options → Chargement/enregistrement → Générale, éditez la ligne "Enregistrer les informations de récupération automatique toutes les" et configurez à une minute.
Cocher la ligne "Toujours créer une copie de sauvegarde".

3. Aller dans Outils → Options → Paramètres linguistiques → Langues, par défaut sur Libreoffice quand on appuie sur le point du clavier numérique cela nous affiche une virgule pour rectifier cela il faut décocher la case "Identique au paramètre de la locale(,)".

## Commandes permettant d'enregistrer l’activité du terminal
* script.
* asciinema.

## Afficher l'aide
- man 
- info
- tldr
- cheat

## faire une capture d'écran avec "the Gimp"
* fichier > créer > capture d'écran

## Mes applications linux en ligne de commande

### Editeur de texte
- vim
- nano

### calculs
bc

### gestion des disques
cfdisk
ncdu

### monitorer
htop

### musique
musikcube

### vidéos
mplayer
mplayer -vo caca  	asscii

### gestionnaire de fichiers
ranger

### archives
tar
zip

### calendrier
date
cal

### agenda
calcurse

### images
feh
cacaview	asscii

### navigateur internet
elinks
browsh

### téléchargements internet
wget
curl

### spotify
spotify-tui

### youtube
yewtube

### edition vidéos
ffmpeg

### slides
slides

### todo listes
taskwarrior-tui

### maps
mapscii

### image du jour de la nasa
nasa-cli, nasa -t

### google trad
translate-shell

### jeux
nsnake

## Mes logiciels 
Czkawka
permet de supprimer des fichiers inutiles, de supprimer des doublons, dossiers vides, gros fichiers, fichiers temp, images similaires, vidéos similaires, musique similaire, liens symboliques invalides, fichiers cassé, fichiers avec la mauvaise extension.
https://github.com/qarmin/czkawka/blob/master/instructions/Instruction.md

GDebi
permet d'installer des .deb en gui et rapide

navigateur web dans le terminal
https://github.com/fathyb/carbonyl

recoll
retrouver des documents perdus
https://www.lesbonscomptes.com/recoll/pages/index-recoll.html

ttyd
partage de term en ligne
https://tsl0922.github.io/ttyd/

Récupération de données perdue ou supprimées ou endommagées
ddrescue

un paint en terminal
pip install --upgrade pipx
pipx install textual-paint
textual-paint --theme dark --language fr --backup-folder ~/img
https://github.com/1j01/textual-paint

Whoogle
un moteur de recherche privée
https://sempreupdate.com.br/guia-para-instalacao-e-uso-do-whoogle-search/

gestion parc info
https://www.howtoforge.com/how-to-install-fleet-osquery-manager-on-rocky-linux-9/
et aussi cockpit

un serveur perso avec pleins d'application dedans comme umbrel ou yonohost

Tipi
gérer et lancer plusieurs outils ou services

installation
sudo curl -L https://setup.runtipi.io | bash
https://runtipi.io/docs/getting-started/installation

flatsweep
nettoyer les flatpak
flatpak install io.github.giantpinkrobots.flatsweep

Umbrel OS
https://umbrel.com/#umbrelos

ouvrir des fichiers à risque sans risque
https://dangerzone.rocks/

conteneurisation d'applications
https://www.kasmweb.com/
https://www-develop.kasmweb.com/downloads.html

gestionnaire de fichiers
ranger

waydroid
émulateur android

bootles
faire tourner des applications windows sur linux
https://usebottles.com/

## Anciens modernes commandes Linux
utiliser tldr , cheat ou tealdeer au lieu de man
utiliser pipx au lieu de pip
utiliser exa au lui de ls
utiliser ncdu au lieu de du
utiliser bat au lieu de cat
utiliser ss
utiliser ip 
utiliser fd au lieu de find

## Automatiser les clics avec xdotool
sudo apt install xdotool

## Navigateur en cli sur linux avec images pixel
```bash
install
wget https://github.com/browsh-org/browsh/releases/download/v1.8.0/browsh_1.8.0_linux_amd64.deb
sudo apt install ./browsh_1.8.0_linux_amd64.deb
rm ./browsh_1.8.0_linux_amd64.deb
browsh
browsh https://www.tecmint.com
```

## 5 outils pour créer ma propre distribution
https://www.linux-live.org/
https://www.linuxfromscratch.org/
https://chris-lamb.co.uk/projects/live-magic
https://www.yoctoproject.org/
https://studioexpress.opensuse.
