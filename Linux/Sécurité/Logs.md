## Récupération des alertes 
```Bash
sudo dmesg | grep -Ei 'warning|critical|error|alert|invalid|failure|fatal'
sudo grep -Ei 'warning|critical|error|alert|invalid|failure|fatal' /var/log/syslog 
```