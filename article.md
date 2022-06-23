---
title: |
  "Graphes sous Python."
date: June, 2022
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
5.  Conclusion


#       1. Python langage favori en science (des données) : Pourquoi ? 

Connu aujourd’hui comme étant un langage de programmation incontournable en data science, Python doit son succès à sa vaste communauté d’internautes très active et aux nombreuses bibliothèques (Numpy, Pandas, PyTorch etc.) scientifiques qu’il contient. Du fait qu’il autorise la programmation orientée objet et la programmation fonctionnelle, Python peut être considéré comme étant flexible et multi paradigmes. De plus, il combine une puissance remarquable avec une syntaxe très claire. Il peut aussi être utilisé comme langage d'extension pour les applications nécessitant une interface programmable. Enfin, Python est portable : il fonctionne sous différents systèmes d’exploitation comme Linux, macOS, et Windows.



#       2.  Éléments de la théorie des graphes 

## Graphes : Une introduction ! 

### Exemple introductif:

Il est 16H30 sur Dakar. Mia, étudiante au DIT, se trouve chez elle où le chargeur de son PC vient de lâcher. Pas de chance, le cours de Python est programmé ce soir à 18H. Elle doit donc se rendre dans un magasin afin d’acquérir un nouveau chargeur avant de se rendre en cours. Comme il est possible de le voir sur le graphe associé, plusieurs voies plus ou moins encombrées (embouteillages) sont praticables pour ce faire.


![](https://raw.githubusercontent.com/AfiaFaith/literate-pancake/87ccd787e477fcb35c6694041226945695b5dcd0/img/Im1.png) 


#### Mia se pose naturellement la question suivante :  Quel est le plus rapide ?

La théorie des graphes propose des solutions à cette classe de problèmes (et à bien plus encore). Elle peut être définie comme une discipline à l’intersection de l’informatique et des mathématiques qui vise à résoudre divers problèmes réels qui induisent des relations entre entités. Les entités sont appelées nœuds ou sommets, les relations sont appelées dans le cas orienté arc sinon, arêtes. Les graphes sont couramment représentés par une matrice ou une liste d’adjacence.


#### Matrice d’adjacence du graphe ci-dessus: 


![](https://raw.githubusercontent.com/AfiaFaith/literate-pancake/87ccd787e477fcb35c6694041226945695b5dcd0/img/Im2.png) 


### Quelques définitions : 

* Dictionnaire Python: est une collection qui associe une clé à une valeur.

* Collection en Python : est un module python intégré qui fournit des types de données de conteneur utiles. Les types de données de conteneur nous permettent de stocker et d'accéder aux valeurs de manière pratique.

* Graphe: est une représentation picturale d'un ensemble d'objets où certaines paires d'objets sont reliées par des liens . Les objets interconnectés sont représentés par des points appelés sommets et les liens qui relient les sommets sont appelés arêtes.

* Structures de données: sont des moyens spécifiques d'organiser et de stocker des données afin qu'elles puissent être consultées et travaillées de manière efficace.

* Matrice: est une structure de données bidimensionnelle dans laquelle les nombres sont organisés en lignes et en colonnes.

* Algorithme: est une suite finie d'instructions, écrites en langage naturel, qui peuvent être exécutées les unes à la suite des autres pour résoudre un problème. L'algorithme ne dépend pas du langage de programmation dans lequel il sera traduit, ni de la machine qui exécutera le programme.

* Méthode: est une fonction qui "appartient à" un objet.


 
#         3. Structures de données python pour les graphes:

## Les graphes avec python:


Il existe plusieurs implémentations de la représentation des graphes en Python. Ces derniers peuvent aussi être considérés comme des structures de données. 


### Liste et Matrice d’adjacence:

Guido Van Rossum, le père de Python, suggère que les dictionnaires sont une bonne implémentation des listes d’adjacence en Python. Pour ce qui est des matrices d’adjacence, plusieurs structures de données peuvent permettre leur représentation à savoir : les listes imbriquées, les tableaux numpy (ndarray) ou encore les data frames pandas.  
Il faut par ailleurs noter qu’il apparaît plus rigoureux de créer une classe permettant de construire un graphe de bout en bout. 


### Liste d’adjacence -> Dictionnaire Python: 

```python
# Représentation d'un graphe avec des dictionnaires 
# Chaque clé représente un noeud/sommet (vertices)

graph = { "MaisonMia" : {"Banque": 20, "DIT":25, "Magasin":25 },
          "Banque" : {"MaisonMia":20, "Magasin":15},
          "Magasin" : {"MaisonMia":20, "Banque":15,"DIT":45},
          "DIT" : {"MaisonMia":10, "Magasin":45}                 
        }

```


### Architecture d’une classe Graph: 

```python
import sys
 
class Graph(object):
    def __init__(self, nodes, init_graph):
        self.nodes = nodes
        self.graph = self.construct_graph(nodes, init_graph)
        
    def construct_graph(self, nodes, init_graph):
        '''
        This method makes sure that the graph is symmetrical. 
        In other words, if there's a path from node A to B with a value V, 
        there needs to be a path from node B to node A with a value V.
        '''
        graph = {}
        for node in nodes:
            graph[node] = {}
        
        graph.update(init_graph)
        
        for node, edges in graph.items():
            for adjacent_node, value in edges.items():
                if graph[adjacent_node].get(node, False) == False:
                    graph[adjacent_node][node] = value
                    
        return graph
    
    def get_nodes(self):
        "Returns the nodes of the graph."
        return self.nodes
    
    def get_outgoing_edges(self, node):
        "Returns the neighbors of a node."
        connections = []
        for out_node in self.nodes:
            if self.graph[node].get(out_node, False) != False:
                connections.append(out_node)
        return connections
    
    def value(self, node1, node2):
        "Returns the value of an edge between two nodes."
        return self.graph[node1][node2]

```

### Algorithme de Moore-Dijkstra:

Du nom de l'informaticien néerlandais Edsger Dijkstra et publié en 1959,  cet algorithme est de complexité polynomiale. Pour n sommets et a arcs, le temps d’exécution est O((a+n)log(n)). 
 


### Principe : 

![](https://raw.githubusercontent.com/AfiaFaith/literate-pancake/87ccd787e477fcb35c6694041226945695b5dcd0/img/im3.png) 



```python
def dijkstra_algorithm(graph, start_node):
    unvisited_nodes = list(graph.get_nodes())
 
    # We'll use this dict to save the cost of visiting each node 
    # and update it as we move along the graph   
    shortest_path = {}
 
    # We'll use this dict to save the shortest known path to a node found so far
    previous_nodes = {}
 
    # We'll use max_value to initialize the "infinity" value of the unvisited nodes   
    max_value = sys.maxsize
    for node in unvisited_nodes:
        shortest_path[node] = max_value
    # However, we initialize the starting node's value with 0   
    shortest_path[start_node] = 0
    
    # The algorithm executes until we visit all nodes
    while unvisited_nodes:
        # The code block below finds the node with the lowest score
        current_min_node = None
        for node in unvisited_nodes: # Iterate over the nodes
            if current_min_node == None:
                current_min_node = node
            elif shortest_path[node] < shortest_path[current_min_node]:
                current_min_node = node
                
        # The code block below retrieves the current node's neighbors 
        # and updates their distances
        neighbors = graph.get_outgoing_edges(current_min_node)
        for neighbor in neighbors:
            tentative_value = shortest_path[current_min_node] + graph.value(current_min_node, neighbor)
            if tentative_value < shortest_path[neighbor]:
                shortest_path[neighbor] = tentative_value
                # We also update the best path to the current node
                previous_nodes[neighbor] = current_min_node
 
        # After visiting its neighbors, we mark the node as "visited"
        unvisited_nodes.remove(current_min_node)
    
    return previous_nodes, shortest_path

```

```python
def print_result(previous_nodes, shortest_path, start_node, target_node):
    path = []
    node = target_node
    
    while node != start_node:
        path.append(node)
        node = previous_nodes[node]
 
    # Add the start node manually
    path.append(start_node)
    
    print("We found the following best path with a value of{}.".format(shortest_path[target_node]))
    print(" -> ".join(reversed(path)))

```


#        4.  Problème du plus court chemin et application:


## Solution au problème de Mia:

Les algorithmes du plus court chemin permettent, étant donné un sommet fixé dans un graphe, de déterminer le plus court chemin (au sens des poids) entre ce dernier et chacun des autres sommets. Le problème de Mia étant d’effectuer un certain parcours (Maison -> Magasin -> DIT) en un temps minimum, il requiert de trouver le plus court chemin entre la Maison et le Magasin puis entre le Magasin et le DIT. Il suffira donc de mettre en œuvre un algorithme du plus court chemin 02 fois et de se servir des résultats pour former le parcours idéal pour Mia. 


## Implémentation Python: 


```python
noeuds = ["MaisonMia","Banque","Magasin","DIT"]
 
init_graph = {}
for noeud in noeuds:
    init_graph[noeud] = {}
    
init_graph["MaisonMia"]["Banque"] = 20
init_graph["Banque"]["Magasin"] = 15
init_graph["Magasin"]["DIT"] = 45
init_graph["Magasin"]["MaisonMia"] = 25
init_graph["DIT"]["MaisonMia"] = 10

graph0 = Graph(noeuds,init_graph)
previous_nodes, shortest_path = dijkstra_algorithm(graph0,"MaisonMia")
print_result(previous_nodes, shortest_path,"MaisonMia","Magasin")

previous_nodes, shortest_path = dijkstra_algorithm(graph0,"Magasin")
print_result(previous_nodes, shortest_path,"Magasin","DIT")

```


#        5.  Conclusion:

Somme toute, il est possible de souligner qu'au moyen de la théorie des graphes, des données sur les trajets et de la flexibilité de Python, une solution viable au problème d’itinéraire de Mia peut être proposée notamment grâce aux implémentations d’une classe Graph et d’un algorithme du plus court chemin (Moore-Dijkstra). 


## Plus court chemin:

```python
# Nous avons trouvé le meilleur chemin suivant avec une valeur de 25.
# MaisonMia -> Magasin
# Nous avons trouvé le meilleur chemin suivant avec une valeur de 35.
# Magasin -> MaisonMia -> DIT
```


#        Ressources : 

* [Application des graphes en Python](https://python-course.eu/applications-python/graphs-python.php)

* [Algorithme de Dijkstra dans un graphe](https://128mots.com/index.php/2020/02/17/lalgorithme-de-dijkstra-dans-un-graphe-pondere-et-oriente-en-plus-de-128-mots/)

* [Implementation Python de l'algorithme de Dijkstra](https://128mots.com/index.php/2020/02/18/implementation-python-de-lalgorithme-de-dijkstra/)

* [Implementation Python de l'algorithme de Bellman Ford](https://128mots.com/index.php/2021/03/01/implementation-python-de-lalgorithme-de-bellman-ford/)

* [Algorithme de Kruskal Python](https://128mots.com/index.php/2021/03/23/algorithme-de-kruskal-python/)

* [Bellman Ford Algorithm](https://favtutor.com/blogs/bellman-ford-python)

* [Bellman Ford Algorithm]( https://www.geeksforgeeks.org/bellman-ford-algorithm-dp-23/)

* [Graph data structure and algorithms](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/)
