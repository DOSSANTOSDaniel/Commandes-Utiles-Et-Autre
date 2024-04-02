## Récupération de certaines informations du système

### UID de l'utilisateur courant
```bash
cat /proc/self/loginuid
```

### Type de l'OS
```bash
cat /proc/sys/kernel/ostype
```

### Version du noyau Linux
```bash
cat /proc/sys/kernel/osrelease
```

### Version de la distribution
```bash
cat /proc/sys/kernel/version
```

## Liste des gestionnaires de paquets sous Linux et la commande pour afficher les logiciels installés
| Gestionnaire de paquets | Commande |
|---|---|
| RPM | `rpm -qa --last` |
| YUM | `yum list installed` |
| DNF | `dnf list installed` |
| Zypper | `zypper se --installed-only` |
| Pacman | `pacman -Q` |
| DPKG | `dpkg -l` |
| APT | `apt list --installed` |

## Supprimer les anciens noyaux Linux sur Ubuntu/Debian
```Bash
sudo apt list --installed | grep -i linux-image
sudo apt remove linux-image-*****
```

## Afficher un message de connexion
1. Utilisation du fichier issue.net (/etc/issue.net)
   * Affiche un message d'avertissement avant la connexion sur une session.

2. Utilisation du fichier MOTD (/etc/motd)
   * Affiche un message de bienvenue après le login de l'utilisateur.

## Afficher la version de sa distribution Linux
|Commande|Distribution|
|---|---|
|cat /etc/os-release|Debian, Ubuntu, Mint, RHEL, CentOS, Fedora, Rocky Linux, AlmaLinux, Alpine Linux, Arch Linux|
|cat /etc/gentoo-release|Gentoo Linux|
|cat /etc/SuSE-release|OpenSUSE|

```Bash
hostnamectl
```

```Bash
cat /etc/issue
```

Sur Ubuntu
```Bash
cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.1 LTS"
```

Exemple avec Ubuntu
```Bash
lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy
```

Sur Debian
```Bash
cat /etc/debian_version

bookworm/sid
```

## Supprimer les caractères DOS(^M) à l'aide de VIM
```Bash
:set ff=unix
```

## Démarrer un processus puis le détacher du terminal
1. Exécution du processus.
```Bash
 sleep 100
```
2.  Interruption du processus.
   'Ctrl + z'

3. Mettre le processus en tache de fond.
```Bash
bg
```

4.  Afficher les processus en tache de fond dans le but d'obtenir leur PID.
```Bash
jobs
```

5. Détacher le processus.
```Bash
disown %<PID>

exit
```

## Afficher les services sur le système
```Bash
service --status-all
```

```Bash
systemctl --type=service --state=running

systemctl --type=service --state=running | grep 'snapd'

systemctl --type=service --state=inactive

systemctl list-unit-files --type=service
```

## Installation de polices de caractères sur Linux

### FontAwesome sur Ubuntu 22.04
```Bash
git clone --depth 1 https://github.com/FortAwesome/Font-Awesome

sudo mkdir -p /usr/share/fonts/Font-Awesome

sudo mv ${PWD}/Font-Awesome/otfs/* /usr/share/fonts/Font-Awesome

rm -rf ${PWD}/Font-Awesome

fc-cache -fv
```

### Gestion des polices de caractères
| Commande  | Description  |
|:---:|:---:|
| `fc-list` | Affiche la liste les polices de caractères installées sur le système. |
| `fc-list :charset=(caractère en hexadécimal)` | Permet de savoir quelle font du système utilise tell caractère. |

## Phrases en vocal sur le terminal
```bash
espeak -s 145 -v fr "+Je vous souhaite une bonne journée !"
```
* -s: vitesse de lecture
* -v: langue

### On peut aussi utiliser `say`
```Bash
say "Hello!"
```

## Afficher une image à partir du terminal
```Bash
eog img.png
display img.png
xdg-open img.png ou open img.png
```

## Effacer l'historique des commandes sur la session courante
```Bash
history -c
```

## Recherche de multiples occurrences avec la commande `grep`
```Bash
grep -E '100|400' toto.txt 
```

## Envoi de messages entre sessions sur le même ordinateur
Afficher les utilisateurs connectés.
```Bash
fuser -v /dev/pts/*
```

Afficher le nom du terminal.
```Bash
tty
```

Envoyer un message.
```Bash
echo "proute" > /dev/pts/<n>
```
* <n> c'est le numéro du terminal virtuel.

## Afficher l'heure et la date sur chaque ligne de l'historique des commandes
```Bash
nano ~/.bashrc
```

```Bash
export HISTTIMEFORMAT="%F %T  "
```

```Bash
source ~/.bashrc
```

## Quel fichier est ouvert par des utilisateurs ou services
Qui utilise le fichier /dev/null.
```Bash
lsof /dev/null
```

Quels fichiers l’utilisateur Daniel utilise.
```Bash
lsof -u daniel
```

Recherche par PID.
```Bash
lsof -p 5857
```

Lister tous les fichiers ouverts.
```Bash
lsof
```

## Synchronisation automatique de l’heure sur Debian
```Bash
 apt install ntp
 ```
 
 ```Bash
 apt install ntpdate
 ```
 
 ```Bash
 ntpdate pool.ntp.org
 ```
 
 ```Bash
 service ntp start
 ```

## Utilisation de la commande script pour enregistrer une session de terminal
* Script est une commande permettant de rediriger la sortie de votre session dans un fichier l'affichage sera de type ascii.

* Dans le but de revoir toutes les étapes faites un peu comme une vidéo, cela ne ré-exécute pas les commandes !

|Option|Description|
|---|---|
|-a|Permet d'ajouter nouvelles commandes et de rediriger la sortie ver un fichier.|
|-q|Cacher les informations de démarrage et de fin de script.|
|--t|Enregistrer les information de temps, cela crée un fichier de temps.|

Pour démarrer une session.
```Bash
script --t=timefile -q scriptfile
```

Ajouter des nouvelles commandes au script précédent
```Bash
script --t=timefile -q -a scriptfile
```
* ^d pour sortir du script

Rejouer le script.
```Bash
scriptreplay --timing=timefile scriptfile
```

* Vitesse de lecture, l'option -d permet de diviser la vitesse par le numéro choisie.
```Bash
scriptreplay --divisor 2 --timing=timefile scriptfile
```

## Afficher le temps d’exécution d'une commande
```Bash
time sleep 5


real	0m5,004s
user	0m0,002s
sys	0m0,001s
```

## Changer la langue du clavier
* Chargez le mappage du clavier sur le noyau Linux.
```Bash
loadkeys fr
```

* Configurer le clavier à l'aide du serveur d'affichage.
```Bash
setxkbmap fr
```

## Lister certains dossiers sauf un, (snap)
```Bash
ls -d *[!snap]*
```

## Afficher le type de fichier
```Bash
file -b --mime-type Images/Captures\ d’écran/test.png
```

## Savoir si une commande existe sur le système
```Bash
command -v sudo
```

## Configurer le pourcentage de mémoire à la suite de laquelle on active le swap
```Bash
echo "vm.swappiness = 10" >> /etc/sysctl.conf
```

## Réduire le nombre de consoles au démarrage
```Bash
sed -i -e "s/ACTIVE_CONSOLES="/dev/tty[1-6]"/ACTIVE_CONSOLES="/dev/tty[1-2]"/g" /etc/default/console-setup
```

## Dossier où placer les fichiers d'Installations de paquets par les sources
```Bash
/usr/local/src
```

## Lancer une commande en arrière plan
```Bash
sleep 60 &
```
* Le processus est attaché à la console, si la console est fermé le processus est tué.

### Détacher le processus de la console.
Lancer le processus avec "nohup".
```Bash
nohup sleep 60
```

* Taper ^+Z pour mettre le processus en pause.

Mettre le processus en arrière plan.
```Bash
bg
```

Afficher les processus en arrière plan.
```Bash
jobs
```

Remettre le processus au premier plan. 
```Bash
fg %1
```

Exemples.
```Bash
nohup sleep 60

nohup: les entrées sont ignorées et la sortie est ajoutée à 'nohup.out'
```

```Bash
^Z[1]   Fini                    sleep 60

[2]+  Arrêté                nohup sleep 60
```

```Bash
bg

[2]+ nohup sleep 60 &
```

```Bash
jobs

[2]+  En cours d'exécution   nohup sleep 60 &
```

```Bash
fg %2

nohup sleep 60
```

## Afficher les différents shells installés sur le système
```Bash
cat /etc/shells
```

* Changer de shell
```Bash
chsh -s sh
```

## Rechercher le chemin de certains fichiers exécutables
```Bash
which pwd
```

```Bash
whereis pwd
```

## Afficher l'utilisation CPU et mémoire des 20 processus consommant le plus de mémoire et de ressources CPU 
```Bash
ps -eo user,pid,comm,%mem,%cpu --sort=-%cpu,-%mem | head -20
```

## Comment savoir si vous avez wayland ou x11
```Bash
echo $XDG_SESSION_TYPE
```

## Afficher la résolution de l’écran
```Bash
xrandr -q | grep \*
```

## Afficher l'âge de l’installation de la distribution Linux
```Bash
stat / | awk '/Créé/ {print $2}'
```

## Vérifier le système init en fonctionnement sur votre distribution
```Bash
ps -q 1 -o comm=
readlink /sbin/init
```Bash

## Epoch
Il existe un système temporel appelé temps d'époque
L'heure d'époque Linux ou heure UNIX c'est le nombre de secondes écoulées depuis 00:00:00, temps universel coordonné(UTC), le jeudi 1er janvier 1970, cette date est devenue le point de départ

Afficher la date et heure actuelle en secondes
```Bash
date +%s
```

Convertir lecture humaine
```Bash
date -d @$(date +%s)
```

Calculer le décalage horaire
```Bash
echo '1698919916 - 1698920240' | bc
```

## Utiliser le presse papier en cli
```Bash
sudo apt install emboss
ls | yank -l
```

## Supprimer les dossiers et fichiers vides
```Bash
find /path/to/dir -empty -type d -delete
find /path/to/dir -empty -type f -delete
```

## Effacer un fichier
Par redirection
```Bash
> toto.txt
echo "" > fichier.txt” ou “echo > fichier.txt
```

Avec dd
```Bash
dd if=/dev/null of=fichier.txt
```

Spécification de la taille
```Bash
truncate -s 0 fichier.txt
```

## Messages entre utilisateur avec wall
Deux users connectés au meme serveur en cli peuvent envoyer des messages avec wall
```Bash
wall [-n] [-t délai] [-g groupe] [message | fichier]
```
Options
-n : supprime la bannier
-t : délai
-g : limite l’affichage aux groupes n

```Bash
wall -n ‘Salut mon amis !’
```
