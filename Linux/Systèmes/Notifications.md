## Notification popup

### Commandes
- notify-send
- xmessage

### Exemples
```Bash
xmessage -buttons Continuer:0,Quitter:1 -center -print "$(lsblk)"
```

```Bash
notify-send "Mon IP" "$(hostname -I)"
```

### Avec l'utilisation d'une image avec l'extension .png
```Bash
notify-send -i "/home/daniel/Images/angry.png" "Mon IP" "$(hostname -I)"
```

### Utilisation d'une image appartenant à une application du système
```Bash
notify-send "Test1" --icon=gedit --app-name="Gedit" "Bonjour"
```

Autres exemples
```Bash
notify-send "$(hostname -I)"
kdialog --msgbox "trsrgf"
notify-send 'text'
```
