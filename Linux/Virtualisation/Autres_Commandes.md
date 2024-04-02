# Virtualisation et conteneurisation

## Savoir si on est dans une machine virtuelle ou une machine physique

### Avec la commande dmidecode
```bash
sudo dmidecode -s system-manufacturer
```

### Avec la commande lshw
```bash
sudo lshw -class system | grep fabricant
```

### Avec la commande hostnamectl
```bash
hostnamectl chassis
```

### Avec la commande systemd-detect-virt
```bash
sudo systemd-detect-virt
```

### Avec la commande virt-what
```bash
sudo virt-what
```

### Avec la commande facter
```bash
facter virtual
```