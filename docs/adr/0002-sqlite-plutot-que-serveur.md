# ADR 0002 : SQLite plutôt qu'un fichier JSON ou un serveur PostgreSQL

- Statut : proposé
- Date : 2026-10-05
- Décideurs : lrodrigues-cyber

## Contexte
Biblio doit stocker des livres, des membres et des prêts. Les utilisateurs sont des bénévoles d'une association : ils installent le programme eux-mêmes, sur leurs propres postes, sans compétence technique particulière. Deux bénévoles peuvent enregistrer un prêt presque en même temps, et les données ne doivent pas être corrompues dans ce cas. Il faut donc choisir comment stocker les données.

## Options envisagées
1. **Un fichier JSON**
   - Pour : très simple à lire et à modifier, aucune dépendance.
   - Contre : le fichier est réécrit en entier à chaque modification ; deux écritures simultanées peuvent le corrompre, et il n'y a pas de requêtes (tout se filtre à la main).
2. **Un serveur PostgreSQL**
   - Pour : très robuste, gère bien de nombreux utilisateurs en même temps.
   - Contre : il faut installer et administrer un serveur, ce qui est trop lourd pour des bénévoles.
3. **SQLite**
   - Pour : une vraie base SQL dans un seul fichier, fournie avec Python, sans installation ni serveur.
   - Contre : peu adaptée à beaucoup d'écritures simultanées, et pas d'accès à distance.

## Décision
Nous utilisons SQLite, car elle offre une vraie base SQL sans rien à installer.

## Conséquences
- Plus facile : l'installation se résume à lancer `python3 biblio.py init` ; les recherches et les jointures passent par SQL ; la sauvegarde consiste à copier un seul fichier.
- Plus difficile : si l'association grandit et que beaucoup de personnes écrivent en même temps, il faudra migrer vers un serveur ; les requêtes écrites en SQL demandent de la rigueur (voir les requêtes paramétrées).