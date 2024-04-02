## Afficher l'ip publique
```Powershell
$PubAddress = (Invoke-WebRequest -Uri "https://ifconfig.me/ip" -UseBasicParsing).Content
Write-Host "IP Publique : $PubAddress"
```

## Afficher l'ip local
```Powershell
Get-NetIPConfiguration | findstr 'IPv4Address'
```
