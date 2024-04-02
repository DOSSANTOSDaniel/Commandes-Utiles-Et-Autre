## Tester un serveur web
```Bash
wget --spider dsjdf.fr
```

```Bash
site='google.fr'
if wget --spider $site 2> /dev/null; then echo "Site UP"; else echo "Site down"; fi
```
