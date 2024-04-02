## Afficher des commandes par rapport à leurs fonctionnalités

### Exemple je cherche une commande pour travailler avec un lecteur Markdown
```bash
man -k 'markdown'

HTML::FormatMarkdown (3pm) - Format HTML as Markdown
mdp (1)              - A command-line based markdown presentation tool
```

## Afficher les autres pages des manuels

### Exemple avec la page 5 de passwd
```Bash
man passwd.5
```

## Exporter en pdf les pages de manuel
```Bash
sudo apt install groff
man -Tpdf ls > ls.pdf
```

## Aide en ligne
```Bash
curl cheat.sh/read
```

## Aide avec exemples

### Pages d'aide maintenues par la communauté qui contiennent des exemples d'utilisation.

### Installation
```Bash
sudo apt install tldr
```

### Mise à jour des données
```Bash
tldr -u
```

## Afficher la description de la hiérarchie des fichiers sur Linux
```Bash
man hier
```
