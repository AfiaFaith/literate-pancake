---
title: |
  "Graphes sous Python."
date: May, 2022
lang: en-EN
urlcolor: blue
geometry: "left=2.5cm,right=2.5cm,top=3cm,bottom=3cm"
documentclass: article
fontfamily: Alegreya
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhf{}
    \rhead{Dakar Institute of Technology}
    \lhead{Afi EDOH et Kidam BALLE}
    \rfoot{Page \thepage}
    \hypersetup{pdftex,
            pdfauthor={Afi EDOH et Kidam BALLE},
            pdftitle={Python programming},
            pdfsubject={Graphes sous Python},
            pdfkeywords={Python, Programming, Graphes, Distance},
            pdfproducer={Emacs, Pandoc, Latex, Markdown},
            pdfcreator={Emacs, Pandoc, Latex, Markdown}}
    
---

# Sommaire:

1.  Python langage favori en science (des données) : Pourquoi ?
2.  Éléments de la théorie des graphes 
3.  Structures de données python pour les graphes
4.  Problème du plus court chemin et application 


            1.  Python langage favori en science (des données) : Pourquoi ? 

Connu aujourd’hui comme étant un langage de programmation incontournable en data science, Python doit son succès à sa vaste communauté d’internautes très active et aux nombreuses bibliothèques (Numpy, Pandas, PyTorch etc.) scientifiques qu’il contient. Du fait qu’il autorise la programmation orientée objet et la programmation fonctionnelle, Python peut être considéré comme étant flexible et multi paradigmes. De plus, il combine une puissance remarquable avec une syntaxe très claire. Il peut aussi être utilisé comme langage d'extension pour les applications nécessitant une interface programmable. Enfin, Python est portable : il fonctionne sous différents systèmes d’exploitation comme Linux, macOS, et Windows.


foo bar baz

```python
# module foo.py

a = 42

def bar(x):
    print(x)
```
