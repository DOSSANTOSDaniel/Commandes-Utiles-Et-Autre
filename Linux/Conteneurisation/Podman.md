
## Configuration de systemd pour le démarrage automatique d'un conteneur

Créez un fichier de service systemd pour Heimdall, par exemple heimdall-container.service
```
	[Unit]
	Description=Heimdall Container
	After=network.target

	[Service]
	ExecStart=/usr/bin/podman-compose -f /chemin/vers/heimdall-compose.yml up -d
	ExecStop=/usr/bin/podman-compose -f /chemin/vers/heimdall-compose.yml down
	Restart=always
	User=your_username

	[Install]
	WantedBy=default.target
```
Placez ce fichier dans /etc/systemd/system/.

Activez le service
```Bash
sudo systemctl enable heimdall-container.service
```

Démarrez le service
```Bash
sudo systemctl start heimdall-container.service
```

## Erreur conteneurs
```Bash
podman version
ERRO[0000] User-selected graph driver "vfs" overwritten by graph driver "overlay" from database - delete libpod local files to resolve.  May prevent use of images created by other tools
ERRO[0000] User-selected graph driver "vfs" overwritten by graph driver "overlay" from database - delete libpod local files to resolve.  May prevent use of images created by other tools
Client:   	Podman Engine
```

### solutions
```Bash
rm -rf ~/.local/share/containers/storage/libpod/bolt_state.db
```

Ou si non pour remettre à zéro
```Bash
rm -rf ~/.local/share/containers
```
