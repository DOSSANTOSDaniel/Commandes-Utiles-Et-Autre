
## L'application warp
* Permet des transfères de fichiers chiffrés entre machines en LAN ou WAN.
- https://flathub.org/apps/details/app.drey.Warp
- https://gitlab.gnome.org/World/warp

## Accéder aux fichiers d'une machine distante en utilisant le gestionnaire de fichiers Gnome
1. Ouvrir le gestionnaire de fichiers.
2. Cliquer sur +Autres emplacements.
3. Insérer la ligne suivante `ssh://192.168.1.85:2244/home/daniel` en bas.
4. Cliquer sur entrée 

## Partager le terminal via LAN ou WAN
### En local avec les commandes
- screen
- tmux

### Par internet 
* [tmate](https://tmate.io/)
* [teleconsole](https://www.teleconsole.com/)
* [tsl0922](https://tsl0922.github.io/ttyd/)

## Alternative à SSH
```bash
mosh
```