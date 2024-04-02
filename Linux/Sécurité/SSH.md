## Indications pour sécuriser la configuration du service SSH
* Changer le port par défaut.
* Mise en place de Fail2Ban. 

### Modifier la configuration
```Bash
PermitRootLogin no
AllowUsers <nom_utilisateur>
PermitEmptyPasswords no
MaxAuthTries 3
Protocol 2
X11Forwarding no
AllowTcpForwarding no
```