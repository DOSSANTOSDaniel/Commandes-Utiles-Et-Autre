## Télécharger un dépôt dans un dossier en particulier(/var/www/html/)
```Bash
git -C /var/www/html/ clone https://github.com/ethicalhack3r/DVWA.git
```

## Ajouter un dépôt distant sur github
```Bash
git init --initial-branch=main test_02
git config --global user.name "DOSSANTOSDaniel"
git config --global user.email "dossantosjdf@gmail.com"
git remote add origin https://github.com/DOSSANTOSDaniel/test_02.git
```

## Connexion du pc local à github
```Bash
ssh-keygen -t ed25519 -C "dossantosjdf@gmail.com"
ssh-add -L
```

```Bash
git config --global user.email "dossantosjdf@gmail.com"
git config --global user.name "DOSSANTOSDaniel"
```

```Bash
ssh -T git@github.com
```

## Vérifier la configuration de git
```Bash
sudo git config --list
```
