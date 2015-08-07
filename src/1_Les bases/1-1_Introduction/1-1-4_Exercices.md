Faisons quelques exercices avant de passer au chapitre suivant. Voyons si la notion de flottants est bien comprise. Nous allons vous donner quelques calculs et vous devrez deviner le résultat avant de l'exécuter pour vérifier votre programme. Simple, non ?

Commençons :

- `2 + 3`
- `3.2 + 4`
- `4 / 3`
- `4 / 3.0`
- `4,0 / 3,0`

Jusque là, il n'y a que de petits calculs. Passons à d'autres choses :

- `4.0 % 2.4`
- `5 * (2 + 5)`
- `3 + 2 * (2 + 5))`
- `3(2 + 2) * 3`

Correction :

[[secret]]
| - `2 + 3` donne `5` comme résultat : c'est une addition de deux entiers.
| - `3.2 + 4` donne `7.2`.
| - `4 / 3` donne `1` : c'est une division entre entiers le résultat est donc un entier.
| - `4 / 3.0` donne `1.3333` : lorsque l'on fait une opération entre un entier et un flottant, le résultat 
| est un flottant.
| - `4,0 / 3,0` donne une erreur : le séparateur est le point et non la virgule.
|
| Et pour les autres :
|
| - `4.0 % 2.4` donne étonnement `1.6`. Le reste est calculé pour une division de flottants quand avec 
| d'autres langages on obtiendrait une erreur. 
| - `5 * (2 + 5)` donne `35` : le calcul entre parenthèses est effectué avant la multiplication. Le calcul 
| effectué est donc `5 * 7`.
| - `3 + 2 * (2 + 5))` donne une erreur : une des parenthèses n'est pas ouverte.
| - `3(2 + 2) * 3` donne aussi une erreur : vous ne pouvez pas ne pas écrire de signes, le `*` doit être 
| précisé.