![Newcastle Vikings Logo from Wikipedia by Garethom](https://upload.wikimedia.org/wikipedia/commons/3/33/NewcastleVikingsLogo.PNG)

Ragnulf
=======

Resolution d'un Rubik's Kube - Projet Algorithmique et Programmation INFO3

# Construction d'une base d'heuristiques
Le script `heuristic_builder.py` est un générateur de raccourcis.
Il construit un fichier `json` de la forme :

```json
{
    <suite de mouvements> : <suite de mouvements équivalente mais plus courte>,
    ...
}
```

Il parcourt toutes les combinaisons de mouvements possibles (jusqu'à une
certaine limite) et déduit, pour chaque combinaison, quelle est la
suite `A` de mouvements la plus courte qui y amène.
Ainsi, pour toutes les autres suites `Bi` de mouvements qui amènent au même
état du cube on retient que `Bi` peut être remplacée par `A`.

Lancer le script (prévoir du café pour patienter) :coffee: :

```bash
python heuristic_builder.py --max 5 --output-file shortcuts-5.json
```

- `--max` : la taille max de la suite de mouvements. Défaut : `3`
- `--output-file` : le fichier de sortie. Défaut : `shortcuts.json`

| max | temps d'éxécution¹ | nombre de combinaisons | nombre de raccourcis |
| :-: | :---------------:  | :--------------------: | :------------------: |
| 1   | instantané         | 18                     | 0                    |
| 2   | instantané         | 342                    | 54                   |
| 3   | ~10sec             | 6174                   | 1998                 |
| 4   | ~5min              | 11150                  | 50598                |
| 5   | ~30min             | 2000718                | 1124358              |
| 130 | ?                  | ~10^164                | ?                    |

*¹ Mac-mini i5, 8Go RAM*

Le script utilise le module `multiprocessing` de Python pour répartir le travail
sur les CPUs, tout en ayant des données partagées (dictionnaire des états,
dictionnaire des raccourcis, compteur, etc.).

## Membres :

- CLOCHARD Guillaume
- LANGELIER Arnaud
- MARRUCCI Tom
- LEBLANC Jimmy
- DORE Jimmy
- BILLAUD Quentin
