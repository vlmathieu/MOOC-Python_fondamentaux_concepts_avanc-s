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

+++

# Exercice sur les ensembles

+++

## Exercice - niveau intermédiaire

```{code-cell}
# chargement de l'exercice
from corrections.exo_marine_set import exo_diff
```

### Les données

+++

Nous reprenons le même genre de données marines en provenance de MarineTraffic que nous avons vues dans l'exercice précédent.

```{code-cell}
from corrections.exo_marine_set import abbreviated, extended
```

### Rappels sur les formats

+++

    étendu: [id, latitude, longitude, date_heure, nom_bateau, code_pays...]
    abrégé: [id, latitude, longitude, date_heure]

```{code-cell}
print(extended[0])
```

```{code-cell}
print(abbreviated[0])
```

### But de l'exercice

```{code-cell}
# chargement de l'exercice
from corrections.exo_marine_set import exo_diff
```

Notez bien une différence importante avec l'exercice précédent : cette fois **il n'y a plus correspondance** entre les bateaux rapportés dans les données étendues et abrégées.

Le but de l'exercice est précisément d'étudier la différence, et pour cela on vous demande d'écrire une fonction

```python
diff(extended, abbreviated)
```

qui retourne un tuple à trois éléments :

* l'ensemble (`set`) des **noms** des bateaux présents dans `extended` mais pas dans `abbreviated` ;
* l'ensemble des **noms** des bateaux présents dans `extended` et dans `abbreviated` ;
* l'ensemble des **id** des bateaux présents dans `abbreviated` mais pas dans `extended` (par construction, les données ne nous permettent pas d'obtenir les noms de ces bateaux).

```{code-cell}
# le résultat attendu
result = exo_diff.resultat(extended, abbreviated)

# combien de bateaux sont concernés
def show_result(extended, abbreviated, result):
    """
    Affiche divers décomptes sur les arguments
    en entrée et en sortie de diff
    """
    print(10*'-', "Les entrées")
    print(f"Dans extended: {len(extended)} entrées")
    print(f"Dans abbreviated: {len(abbreviated)} entrées")
    print(10*'-', "Le résultat du diff")
    extended_only, both, abbreviated_only = result
    print(f"Dans extended mais pas dans abbreviated {len(extended_only)}")
    print(f"Dans les deux {len(both)}")
    print(f"Dans abbreviated mais pas dans extended {len(abbreviated_only)}")

show_result(extended, abbreviated, result)
```

### Votre code

```{code-cell}
:latex:hidden-code-instead: diff = exo_diff.solution
:latex:hidden-silent: true

def diff(extended, abbreviated):
    "<votre_code>"
```

### Validation

```{code-cell}
exo_diff.correction(diff, extended, abbreviated)
```

### Des fichiers de données plus réalistes

+++

Comme pour l'exercice précédent, les données fournies ici sont très simplistes ; vous pouvez, si vous le voulez, essayer votre code avec des données (un peu) plus réalistes en chargeant des fichiers de données plus complets :

* [data/marine-e2-ext.json](data/marine-e2-ext.json)
* [data/marine-e2-abb.json](data/marine-e2-abb.json)

Ce qui donnerait en Python :

```{code-cell}
# load data from files
import json

with open("data/marine-e2-ext.json", encoding="utf-8") as feed:
    extended_full = json.load(feed)

with open("data/marine-e2-abb.json", encoding="utf-8") as feed:
    abbreviated_full = json.load(feed)
```

```{code-cell}
# le résultat de votre fonction sur des données plus vastes
# attention, show_result fait des hypothèses sur le type de votre résultat
# aussi si vous essayez d'exécuter ceci avec comme fonction diff
# la version vide qui est dans le notebook original
# cela peut provoquer une exception
diff_full = diff(extended_full, abbreviated_full)
show_result(extended_full, abbreviated_full, diff_full)
```

Je signale enfin à propos de ces données plus complètes que :

* on a supprimé les entrées correspondant à des bateaux différents mais de même nom ; cette situation peut arriver dans la réalité (c'est pourquoi d'ailleurs les bateaux ont un *id*) mais ici ce n'est pas le cas ;
* il se peut par contre qu'un même bateau fasse l'objet de plusieurs mesures dans `extended` et/ou dans `abbreviated`.