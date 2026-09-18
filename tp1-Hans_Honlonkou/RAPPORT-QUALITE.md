# Rapport qualité, module inventaire

Nom : Hans Honlonkou
Date :16/09/2026
Empreinte du commit de départ :

---

## 1. Tableau de bord initial

Mesures relevées avant toute modification.

### Complexité par fonction

| Fonction | Ligne | Complexité cyclomatique | Rang |
|---|---:|---:|---|
| `rapport` | 122 | 22 | D |
| `par_cat` | 94 | 10 | B |
| `mouv` | 37 | 9 | B |
| `classer` | 74 | 5 | A |
| `val` | 19 | 3 | A |
| `alerte` | 29 | 3 | A |
| `cout` | 62 | 3 | A |
| `rot` | 87 | 2 | A |
| `maj_prix` | 175 | 1 | A |
| `export_json` | 185 | 1 | A |

Commande utilisée :

```powershell
radon cc -s -a "inventaire\inventaire.py"
```

### Synthèse du fichier

| Mesure | Valeur | Commande |
|---|---|---|
| Lignes de code réelles | 159 | `radon raw -s "inventaire\inventaire.py"` |
| Complexité moyenne | 5.9, rang B | `radon cc -s -a "inventaire\inventaire.py"` |
| Indice de maintenabilité | A (36.80) | `radon mi -s "inventaire\inventaire.py"` |
| Score pylint | 7.76 / 10 | `pylint "inventaire\inventaire.py"` |
| Problèmes ruff | 14 | `ruff check "inventaire\inventaire.py"` |
| Entrées vulture | 14 | `vulture "inventaire\inventaire.py"` |
| Couverture de branches | 0 %, aucun test collecté | `python -m pytest --cov="inventaire" --cov-branch --cov-report=term-missing` |
| Barrière xenon | échec : fonction D, moyenne B, module B | `xenon --max-absolute B --max-modules A --max-average A "inventaire\inventaire.py"` |

---

## 2. Catalogue des odeurs

Douze entrées minimum. Trois au moins doivent être invisibles pour les outils.
La colonne conséquence décrit ce qui arrive à la personne qui devra modifier ce
fichier dans six mois.

| # | Ligne | Odeur ou défaut | Détecté par | Conséquence concrète |
|---|---|---|---|---|
| 1 | 2-4 | Commentaires de peur et TODO ancien | Revue humaine | Le commentaire avertit du danger sans décrire le comportement vérifiable ; il augmente la peur de modifier `mouv`. |
| 2 | 10-13 | Constantes cryptiques et nombres magiques | Revue humaine | Modifier une règle de remise ou de réapprovisionnement oblige à comprendre la signification de `S`, `R` et `Q`. |
| 3 | 14-16 | État global mutable | Revue humaine / Pylint partiel | Les appels peuvent modifier un état partagé et rendre les tests dépendants de leur ordre. |
| 4 | 19-23 | Nommage cryptique | Revue humaine | Le lecteur doit deviner que `val`, `arts`, `t` et `a` concernent la valeur du stock et les articles. |
| 5 | 22-25 | Branche inutile | Revue humaine | Une branche sans effet fait croire qu’un cas métier est traité alors qu’elle ne modifie pas le total. |
| 6 | 30-33 | Variables trop vagues | Revue humaine | Le contenu de `l` et `a` doit être deviné, ce qui augmente le risque d’ajouter une mauvaise logique. |
---

## 3. Faut-il tout réécrire

Une demi-page. Chiffres de la partie 1, au moins un exemple historique vu en cours,
et un ordre d'intervention justifié.

---

## 4. Écarts constatés entre le code et les règles métier

Rempli pendant la mission 3, sans rien corriger.

| Règle | Ligne | Ce que le code fait | Ce que la règle dit |
|---|---|---|---|
|  |  |  |  |

---

## 5. Tableau de bord après refactoring

Mêmes mesures, mêmes commandes qu'en partie 1.

| Mesure | Avant | Après | Écart |
|---|---|---|---|
|  |  |  |  |

Ce que ce delta prouve, en trois phrases maximum :

---

## 6. Bugs prouvés puis corrigés

| Règle violée | Ligne d'origine | Commit red | Commit fix | Conséquence métier |
|---|---|---|---|---|
|  |  |  |  |  |

Pour au moins un de ces bugs, la conséquence est chiffrée en euros ou en ruptures de stock.
