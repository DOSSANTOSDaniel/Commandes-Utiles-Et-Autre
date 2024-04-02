## Rechercher des occurrences de textes dans un PDF
```Bash
pdfgrep -F 'tot*' file.pdf
```

### Script Bash pour la recherche d'occurrences sur plusieurs fichiers PDF
```Bash
#!/bin/bash

readonly pdf_dir="/home/daniel/Nextcloud/BOOKS/Informatique/G_LINUX/BASH/*/*.pdf"
readonly search_word="linux"

mapfile -t files_tab < <(ls ${pdf_dir})

for pdf_file in "${files_tab[@]}"
do
  echo -e "\nFichier PDF : $pdf_file"
  pdfgrep -n "$search_word"  "$pdf_file"
done
```
