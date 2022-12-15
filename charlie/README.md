# Mais où est Charlie ?

Ce dispositif permet de générer des planches à imprimer dans le cadre d'une animation de découverte de la blockchain, dont [voici un déroulé](https://repeated-fold-0ca.notion.site/Blockchain-humaine-f97a891457fb4cdea8f18fe259c15626).

L'objectif est d'implémenter une preuve de travail *humaine* (non au sens preuve de « travail humain », mais bien « preuve de travail » adaptée aux humains). Il faut une tâche un peu longue à résoudre, mais facile à vérifier. C'est le cas des albums *Mais où Charlie ?*. Trouver Charlie sur une planche prend plusieurs minutes, mais si on nous indique où il est, on peut rapidemment le vérifier. L'objectif est donc de générer des planches de ce style. La solution adoptée, pour être suffisamment simple, est de produire des grilles d'emojis dont seuls certains (une dizaine) n'apparaissent qu'une fois. Une même grille peut donc être utilisée plusieurs fois si nécessaire, ce qui réduit le nombre de feuilles à imprimer.

## Prérequis

Le générateur est implémenté en [Python](https://www.python.org/), et nécessite l'installation de [Inkscape](https://inkscape.org/fr/) et [ImageMagick](https://imagemagick.org/index.php).

Installer ensuite les dépendances Python :

```console
pip install -r requirements.txt
```

## Utilisation

```console
python generate.py
```

Cela génère, par défaut, un document PDF avec toutes les planches à imprimer, ainsi qu'un document TXT avec toutes les solutions.

Pour obtenir de l'aide, utiliser l'argument `-h` ou `--help` :

```console
python generate.py -h
```

### Fusionner et compresser manuellement les planches produites

Si nécessaire, à l'aide de [PDFtk](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/) et [ImageMagick](https://imagemagick.org/index.php).

```console
pdftk 000.pdf 001.pdf 002.pdf 003.pdf cat output merged.pdf
convert -density 900 -quality 70 -compress jpeg merged.pdf merged_compressed.pdf
```