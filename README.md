# Biblio

Biblio gère les prêts de livres d'une association, pour ses bénévoles.

## Prérequis

- Python 3 (testé avec Python 3.12)
- Git
- Un terminal (Linux, macOS, WSL ou Windows)

Aucune bibliothèque externe à installer.

## Installation

1. Cloner le dépôt :

```
git clone https://github.com/lrodrigues-cyber/biblio-taali-isaac-lucas.git
```

2. Ouvrir un terminal dans le dossier du projet :

```
cd biblio-taali-isaac-lucas
```

3. Créer la base de démonstration (à faire une fois, avant toutes les autres commandes) :

```
python3 biblio.py init
```

Résultat obtenu :

```
Base initialisee : 6 livres, 3 membres.
```

Sous macOS, Linux ou WSL : `python3`. Sous Windows, si `python` ne marche pas : `py`.
Sans `init`, les autres commandes échouent avec l'erreur `no such table`.

## Utilisation

Toutes les commandes se lancent depuis le dossier du projet, après `init`.

### Lister les livres

```
python3 biblio.py livres
```

Résultat obtenu :

```
[1] L'Etranger (Albert Camus) : disponible
[2] Dune (Frank Herbert) : emprunte
[3] Le Petit Prince (Antoine de Saint-Exupery) : disponible
[4] Fondation (Isaac Asimov) : disponible
[5] Les Miserables (Victor Hugo) : disponible
[6] Neuromancien (William Gibson) : disponible
```

### Chercher un titre

```
python3 biblio.py chercher Dune
```

Résultat obtenu :

```
[2] Dune (Frank Herbert)
```

### Emprunter un livre

Syntaxe : `emprunter <numéro du livre> <numéro du membre>`

```
python3 biblio.py emprunter 3 1
```

Résultat obtenu :

```
Emprunt enregistre : livre 3, membre 1.
```

### Rendre un livre

Syntaxe : `rendre <numéro du livre>`

```
python3 biblio.py rendre 3
```

Résultat obtenu :

```
Retour enregistre pour le livre 3.
```

### Lister les retards

```
python3 biblio.py retards
```

Résultat obtenu (le nombre de jours change chaque jour) :

```
Dune, emprunte par Alice Martin : 254 jours de retard
Fondation, emprunte par Bilal Haddad : 259 jours de retard
```

### Limites connues

- Chercher un titre avec une apostrophe (`chercher "L'Etranger"`) fait planter la commande.
- Un livre déjà emprunté peut être emprunté une seconde fois.
- `retards` affiche aussi des livres déjà rendus (Fondation a été rendu).

## Tests

```
python3 -m unittest
```

Résultat obtenu (fin de la sortie) :

```
----------------------------------------------------------------------
Ran 4 tests in 0.028s

OK
```

## Structure du projet

- `biblio.py` : le programme (toutes les commandes)
- `tests/` : les tests automatiques
- `docs/` : la documentation (`circulation.md`, décisions dans `docs/adr/`)
- `exercices/` : les consignes des TP
- `.github/` : modèles d'issues, modèle de pull request et tests automatiques
- `biblio.db` : la base de données, créée par la commande `init`

## Contribuer

1. Ouvrir une issue avec le bon modèle (bug, évolution ou question).
2. Créer une branche depuis `main` : `fix/<n°>-mot-cle` ou `docs/<n°>-mot-cle`.
3. Ne jamais pousser directement sur `main`.
4. Ouvrir une pull request avec `Closes #<n°>` dans la description.
5. Faire relire la pull request par une autre personne, puis merger.

## Auteurs

- Lucas ROODRIGUES
- Taali Zengue
- Isaac Ferras