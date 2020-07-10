---
jupytext:
  cell_metadata_filter: all
  notebook_metadata_filter: all,-language_info,-toc,-jupytext.text_representation.jupytext_version,-jupytext.text_representation.format_version
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

<div class="licence">
<span>Licence CC BY-NC-ND</span>
<span>Thierry Parmentelat &amp; Arnaud Legout</span>
<span><img src="media/both-logos-small-alpha.png" /></span>
</div>

```{code-cell}
%load_ext autoreload
%autoreload 2
```

# construire une matrice diagonale

```{code-cell}
import numpy as np
```

On vous demande d'écrire une fonction `matdiag` qui 

1. accepte un paramètre qui est une liste de flottants [$x_1$, $x_2$, …, $x_n$] 
1. retourne une matrice carrée diagonale dont les éléments valent

$$
m_{ii} = x_i 
$$
$$
m_{ij} = 0 \ pour\  i ≠ j
$$

Quelques précisions :

* il est raisonnable de retourner toujours un tableau de type  `float64`
* vous n'avez pas besoin de vérifier que l'appelant passe au moins un paramètre,
  ou dit autrement, les jeux de tests n'essaient pas d'appeler la fonction sans argument.

```{code-cell}
# c'est ce qu'on voit sur cet exemple

from corrections.exo_matdiag import exo_matdiag

exo_matdiag.example()
```

```{code-cell}
# à vous de jouer
def matdiag(liste):
    ...
```

```{code-cell}
exo_matdiag.correction(matdiag)
```

## Indices

Vous trouverez dans les solutions 3 façons d'implémenter cette fonction; elles utilisent respectivement :  

une approche naïve, une approche à base de slicing, et une approche à base d'une fonction prédéfinie dans numpy.