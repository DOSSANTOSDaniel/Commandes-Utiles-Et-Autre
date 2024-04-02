## Installation du serveur ssh
```Powershell
get-windowscapability -online
add-windowscapability -online -name Openssh.Server~~~~0.0.1.0
get-service -DisplayName *ssh*
set-service -name sshd -startuptype automatic
start-service sshd
get-nettcpconnection -LocalPort 22
get-localuser
get-netipaddress
```


