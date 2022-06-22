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


           2.  Éléments de la théorie des graphes 

Graphes : Une introduction ! 

Exemple introductif:

Il est 16H30 sur Dakar. Mia, étudiante au DIT, se trouve chez elle où le chargeur de son PC vient de lâcher. Pas de chance, le cours de Python est programmé ce soir à 18H.  Elle doit donc se rendre dans un magasin afin d’acquérir un nouveau chargeur. Comme il est possible de le voir sur le graphe associé, plusieurs voies plus ou moins encombrées (embouteillages) sont praticables pour ce faire.

![](https://raw.githubusercontent.com/AfiaFaith/literate-pancake/87ccd787e477fcb35c6694041226945695b5dcd0/img/Im1.png) 


Mia se pose naturellement la question suivante :  Quel est le plus rapide ? 


La théorie des graphes propose des solutions à cette classe de problèmes (et à bien plus encore). Elle peut être définie comme une discipline à l’intersection de l’informatique et des mathématiques qui vise à résoudre divers problèmes réels qui induisent des relations entre entités. Les entités sont appelées nœuds ou sommets, les relations sont appelées dans le cas orienté arc sinon, arêtes. Les graphes sont couramment représentés par une matrice ou une liste d’adjacence. 


Matrice d’adjacence du graphe ci-dessus:

![](https://raw.githubusercontent.com/AfiaFaith/literate-pancake/87ccd787e477fcb35c6694041226945695b5dcd0/img/Im2.png) 


Quelques définitions : 


★   Python: est un langage de programmation polyvalent et puissant. C'est une excellente première langue car elle est concise et facile à lire. Quoi que vous vouliez faire, Python peut le faire. Du développement Web à l'apprentissage automatique en passant par la science des données, Python est le langage qu'il vous faut.

★   Dictionnaire Python: est une collection qui associe une clé à une valeur

★   Collection en Python : est un module python intégré qui fournit des types de données de conteneur utiles. Les types de données de conteneur nous permettent de stocker et d'accéder aux valeurs de manière pratique.

★   Graphe: est une représentation picturale d'un ensemble d'objets où certaines paires d'objets sont reliés par des liens. Les objets interconnectés sont représentés par des points appelés sommets et les liens qui relient les sommets sont appelés arêtes.

★   Structures de données: sont des moyens spécifiques d'organiser et de stocker des données afin qu'elles puissent être consultées et travaillées de manière efficace.

★   Matrice: une structure de données bidimensionnelle dans laquelle les nombres sont organisés en lignes et en colonnes

★   Algorithme: est une suite finie d'instructions, écrites en langage naturel, qui peuvent être exécutées les unes à la suite des autres pour résoudre un problème. L'algorithme ne dépend pas du langage de programmation dans lequel il sera traduit, ni de la machine qui exécutera le programme

★   Méthode: est une fonction qui "appartient à" un objet


 
         3.  Structures de données python pour les graphes:

Les graphes avec python:

Il existe plusieurs implémentations de la représentation des graphes en python. (aussi, les graphes peuvent également être considérées comme étant des structures de données). 

Liste et Matrice d’adjacence:

Guido Van Rossum, le père de Python, suggère que les dictionnaires sont une bonne implémentation des listes d’adjacence en Python. Pour ce qui est des matrices d’adjacence, plusieurs structures de données peuvent permettre leur représentation à savoir : les listes imbriquées, les tableaux numpy (ndarray) ou encore les data frames pandas.  
Il faut par ailleurs noter qu’il apparaît plus rigoureux de créer une classe permettant de construire un graphe de bout en bout. 


Liste d’adjacence -> Dictionnaire Python:


```python
# Représentation d'un graphe avec des dictionnaires 
# Chaque clé représente un noeud/sommet (vertices)

graph = { "MaisonMia" : {"Banque": 20, "DIT":25, "Magasin":25 },
          "Banque" : {"MaisonMia":20, "Magasin":15},
          "Magasin" : {"MaisonMia":20, "Banque":15,"DIT":45},
          "DIT" : {"MaisonMia":10, "Magasin":45}                 
        }

```



foo bar baz

```python
# module foo.py

a = 42

def bar(x):
    print(x)
```
