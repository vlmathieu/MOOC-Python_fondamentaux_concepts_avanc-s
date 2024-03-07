---
jupytext:
  cell_metadata_filter: all, -hidden, -heading_collapsed, -run_control, -trusted
  notebook_metadata_filter: all, -jupytext.text_representation.jupytext_version, -jupytext.text_representation.format_version,
    -language_info.version, -language_info.codemirror_mode.version, -language_info.codemirror_mode,
    -language_info.file_extension, -language_info.mimetype, -toc
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
language_info:
  name: python
  pygments_lexer: ipython3
nbhosting:
  title: if et def
---

<div class="licence">
<span>Licence CC BY-NC-ND</span>
<span>Thierry Parmentelat &amp; Arnaud Legout</span>
<span><img src="media/both-logos-small-alpha.png" /></span>
</div>

+++

# Instruction `if` et fonction `def`

+++

## Exercice - niveau basique

+++

### Fonction de divisibilité

+++

L'exercice consiste à écrire une fonction baptisée `divisible` qui retourne une valeur booléenne, qui indique si un des deux arguments est divisible par l'autre.

Vous pouvez supposer les entrées `a` et `b` entiers et non nuls, mais pas forcément positifs.

```{code-cell} ipython3
:tags: []

# par exemple
from corrections.exo_divisible import exo_divisible
exo_divisible.example()
```

```{code-cell} ipython3
def divisible(a, b):
    if (a % b == 0) | (b % a == 0):
        return True
    else:
        return False
```

Vous pouvez à présent tester votre code en évaluant ceci, qui écrira un message d'erreur si un des jeux de test ne donne pas le résultat attendu.

```{code-cell} ipython3
# tester votre code
exo_divisible.correction(divisible)
```

## Exercice - niveau basique

+++

##### Fonction définie par morceaux

On veut définir en Python une fonction qui est définie par morceaux :

+++

$$
f: x \longrightarrow \left\{
\begin{array}{ll}
-x - 5          & \mbox{si } x \leqslant -5 \\
0               & \mbox{si } x \in [-5, 5]  \\
\frac{1}{5}x -1 & \mbox{si } x \geqslant 5  \\
\end{array}
\right.
$$

```{code-cell} ipython3
# donc par exemple
from corrections.exo_morceaux import exo_morceaux
exo_morceaux.example()
```

```{code-cell} ipython3
# à vous de jouer

def morceaux(x):
    if x <= -5:
        return -x-5
    elif x <= 5:
        return 0
    else:
        return 1/5*x-1
```

```{code-cell} ipython3
# pour corriger votre code
exo_morceaux.correction(morceaux)
```

##### Représentation graphique

+++

L'exercice est terminé, mais nous allons maintenant voir ensemble comment vous pourriez visualiser votre fonction.

Voici ce qui est attendu comme courbe pour `morceaux` (image fixe) :
![graphe morceaux](media/morceaux.png)

+++

En partant de votre code, vous pouvez produire votre propre courbe en utilisant `numpy` et `matplotlib` comme ceci :

```{code-cell} ipython3
# on importe les bibliothèques
import numpy as np
import matplotlib.pyplot as plt
```

```{code-cell} ipython3
# un échantillon des X entre -10 et 20
X = np.linspace(-10, 20)

# et les Y correspondants
Y = np.vectorize(morceaux)(X)
```

```{code-cell} ipython3
# on n'a plus qu'à dessiner
plt.plot(X, Y)
plt.show()
```
