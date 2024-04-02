## Affiche des informations sur le matériel
```bash
inxi -Fx
```

## Informations sur le matériel

### Utilisation de la commande `sysctl`
```Bash
sudo sysctl -a hw.model
sudo sysctl -a | grep -i hw.*cpu
sudo sysctl -n net.wlan.devices   # Information sur l'interface Wifi
```

### Utilisation de la commande `dmesg`
```Bash
sudo dmesg | grep CPU
sudo dmesg | grep memory
```

### Utilisation de la commande `dmidecode`
```Bash
sudo dmidecode
sudo dmidecode -t processor
sudo dmidecode -t memory
sudo dmidecode -t bios
sudo dmidecode -t 0
```

#### Tableau des codes a utiliser avec la commande `dmidecode`
```Bash
Code 	Description
0 	BIOS
1 	System
2 	Baseboard
3 	Chassis
4 	Processor
5 	Memory Controller
6 	Memory Module
7 	Cache
8 	Port Connector
9 	System Slots
10 	On Board Devices
11 	OEM Strings
12 	System Configuration Options
13 	BIOS Language
14 	Group Associations
15 	System Event Log
16 	Physical Memory Array
17 	Memory Device
18 	32-bit Memory Error
19 	Memory Array Mapped Address
20 	Memory Device Mapped Address
21 	Built-in Pointing Device
22 	Portable Battery
23 	System Reset
24 	Hardware Security
25 	System Power Controls
26 	Voltage Probe
27 	Cooling Device
28 	Temperature Probe
29 	Electrical Current Probe
30 	Out-of-band Remote Access
31 	Boot Integrity Services
32 	System Boot
33 	64-bit Memory Error
34 	Management Device
35 	Management Device Component
36 	Management Device Threshold Data
37 	Memory Channel
38 	IPMI Device
39 	Power Supply
40 	Additional Information
41 	Onboard Devices Extended Information
42 	Management Controller Host Interface
```

## Commande `acpi`

### Commande permettant d'afficher le pourcentage de la batterie
```Bash
acpi -b
```

### Afficher les informations des sondes de température
```Bash
acpi -t
```

## Affiche des informations concernant le système
```bash
hostnamectl
```

## Afficher l'architecture de notre système
```Bash
getconf LONG_BIT
```

```Bash
arch
```

## Afficher des informations sur le BIOS du système
```Bash
dmidecode -t bios
```

## Afficher le modèle de l'ordinateur
```Bash
sudo  dmidecode |  grep Product
```

## Afficher des informations par rapport au BIOS sur le système
```bash
sudo dmidecode -t bios
```
