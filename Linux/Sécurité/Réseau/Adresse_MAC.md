## Changer son adresse MAC
```Bash
ip link show
```

```Bash
sudo ip link set dev enp1s0 down
```
 
```Bash
sudo ip link set dev enp1s0 address **:**:**:**:**:**
```

```Bash
sudo ip link set dev enp1s0 up
```