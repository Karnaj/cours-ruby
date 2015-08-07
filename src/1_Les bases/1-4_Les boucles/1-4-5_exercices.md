Comme d'habitude, terminons ce chapitre par une petite série d'exercices.

# Exercice 1

Écrivez un programme qui demande un entier $n$ à l'utilisateur et qui affiche la somme des nombres de $1$ à $n$, si $n$ est positif, et retourne une erreur sinon. 

Correction :

[[secret]]
| Pour ce faire, nous allons initialiser une variable `somme` à 0, puis, dans une boucle `for`, ajouter  
| les entiers à cette variable. 
|
| ```ruby
| print "Entrez un nombre positif : "
| n = gets.chomp.to_i
| if n < 0 
|    print "Erreur, votre nombre n'est pas positif" 
| else
|    somme = 0
|    for k in 1..n
|       somme = somme + k
|    end
|    print somme
| end
| ```

# Exercice 2 

Écrire un programme qui demande un entier $n$ à l'utilisateur et affiche un triangle de $n$ lignes composés d'étoiles. Pour $n = 4$, le programme doit afficher 

```
*
**
***
****
```

Correction :

[[secret]]
|
| Le principe est un peu le même que pour l'exercice 1. Cependant, il faut cette fois utiliser deux boucles
| imbriquées. la première pour le nombre de lignes à afficher, la seconde pour le nombre d'étoiles à afficher
| par ligne, et ceci en sachant que lorsqu'on est à la ligne $n$, on affiche $n$ étoiles.
|
| ```ruby
| print "Entrez un entier positif : "
| n = gets.chomp.to_i
| if n < 0
|    print "Votre nombre n'est pas positif"
| else
|    for k in 1..n 
|       for i in 1..k
|          print "*"
|       end
|       puts
|    end
| end  
| ```

# Exercice 3

Vous en avez l'habitude, il faut aussi des exercices compliqués. Ici, nous allons vous demander d'écrire un programme qui demande un nombre **entier** à l'utilisateur et qui affiche ensuite ce nombre à l'envers. Un exemple d'utilisation du programme :

```
Entrez un nombre entier : 1974
4791
```

Aide :

[[secret]]
| L'indice qu'on pourrait vous donner est d'utiliser le modulo. En effet, on a : 
|
| - $4791 \% 10 = 1$ 
| - $479 \% 10 = 9$
| - $47 \% 10 = 7$
| - $4 \% 10 = 4$
|
| Vous pouvez ainsi obtenir tous les chiffres à afficher.

Correction :

[[secret]]
| 
|
| ```ruby
| print "Entrez un nombre : "
| nombre = gets.chomp.to_i
| while nombre != 0
|    print nombre % 10
|    nombre = nombre / 10
| end
| ```
|
| Si vous ne comprenez pas ce programme tout de suite, prenez un nombre, et déroulez l'algorithme sur lui à 
| l'aide d'un crayon et d'un papier.