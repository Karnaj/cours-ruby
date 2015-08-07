C'est l'heure de pratiquer. Nous allons donc faire quelques petits exercices.

# Exercice 1

Commençons par un petit exercice : demandez à l'utilisateur son nom et son prénom et affichez « Bonjour nom prénom » suivie d'un retour à la ligne. 

Correction :

[[secret]]
| Nous allons utiliser deux variables `nom` et `prenom` et demander leur valeur à l'utilisateur, puis les 
| afficher grâce à une interpolation.
|
| ```ruby
| print "Entrez votre nom : "   
| nom = gets.chomp
| print "Entrez votre prénom : "
| prenom = gets.chomp
| puts "Bonjour #{nom} #{prenom}"
| ```
| Vous remarquez que nous avons utilisé `print` quand nous ne voulions pas aller à la ligne et `puts` quand 
| nous voulions aller à la ligne.

# Exercice 2

Vous devez maintenant demander à l'utilisateur d'entrer deux nombres `x` et `y`, échanger la valeur de des deux nombres, et afficher leur nouvelle valeur. Voici ce que nous devons obtenir :

```
Entrez x : 23
Entrez y : 12
L'échange a été effectué : x vaut 12 et y vaut 23 
``` 

[[attention]]
| Le but est de vraiment échanger les valeurs des deux variables, pas juste d'afficher la valeur de l'une pour
| l'autre.

Correction : 

[[secret]]
| La difficulté est l'échange des deux variables. Pour ce faire, nous allons utiliser une variable temporaire
| que nous appellerons `tmp`. Nous stockerons la valeur de `x` dans `tmp`, puis nous affecterons à `x` la 
| valeur de `y` et enfin `y` prendra la valeur de `tmp`.
|
| ```ruby
| print "Entrez x : "
| x = gets.chomp.to_i
| print "Entrez y : "
| y = gets.chomp.to_i
| 
| tmp = x
| x = y
| y = tmp
| print "L'échange a été effectué : x vaut #{x} et y vaut #{y}"
| ```

# Exercice 3

Cette fois, vous devez demander à l'utilisateur son âge en années (un entier)  et afficher sur différentes lignes :

- son âge en années
- son âge en jour (on va considérer que toutes les années ont $365$ jours)
- son âge en heure
- son âge en minutes
- son âge en seconde

Oui, ça va demander plusieurs calculs. Mais c'est bien ça le but.

Correction :

[[secret]]
| Vous pouvez effectuer les calculs de plusieurs manières. Mais, le but est de ne pas faire de calculs 
| inutiles. Ainsi, vous pouvez soit créer plusieurs variables pour contenir l'âge en les différentes unités,
| soit avoir une seule variable et afficher l'âge dans une unité puis la convertir dans l'unité suivante et
| afficher et ce jusqu'à avoir tout affiché.
|
| Dans tous les cas, pour ne pas faire de calculs inutiles, il vaut mieux utiliser le résultat du calcul 
| précédent pour faire le calcul suivant. Il faut donc utiliser l'âge en années pour calculer celui en jours,
| celui en jours pour calculer celui en heure...
|
| Voici le programme, fait des deux manières que nous avons évoqué.
| 
| ```ruby
| print "Entrez votre age : "
| age = gets.chomp.to_i # On convertit la saisie en entier
| puts age
| age = age * 365 # On passe aux jours
| puts age
| age = age * 24 # On passe aux heures
| puts age
| age = age * 60 # On passe aux minutes
| puts age
| age = age * 60 # On passe aux secondes
| puts age
| ```
| 
| Dans celui-ci on affiche la variable age avant de passer à l'unité suivante et ainsi de suite.
|
| Voici le deuxième, dans lequel on va créer des variables pour les jours, les heures, les minutes et les 
| secondes. 
|
| ```ruby
| print "Entrez votre age : "
| age = gets.chomp.to_i # On convertit la saisie en entier
| jours = age * 365
| heures = jours * 24
| minutes = heures * 60
| secondes = minutes * 60
| puts age
| puts jours
| puts heures
| puts minutes
| puts secondes
| ```

# Exercice 4

Finissons avec un exercice pour bien travailler les conversions : Demandez à l'utilisateur deux nombres, puis affichez sur des lignes différentes le résultat de l'addition, de la soustraction, de la multiplication et de la division du premier nombre par le deuxième. Si l'utilisateur rentre $6$ et $4$, le résultat attendu est :

```
6.0 + 4.0 = 10.0
6.0 - 4.0 = 2.0
6.0 * 4.0 = 24.0
6.0 / 4.0 = 1.5 
``` 

L'affichage vous donne déjà un indice : vous devrez utiliser des flottants.

Correction :

[[secret]]
| Nous demandons les deux nombres et les convertissons en flottants, puis nous affichons toutes les 
| données.   
|
| ```ruby
| print "Entrez le premier nombre : "
| nombre1 = gets.chomp.to_f # On demande le nombre 1 et on le convertit en flottant
| print "Entrez le deuxième nombre : "
| nombre2 = gets.chomp.to_f # On demande le nombre 1 et on le convertit en flottant
| 
| puts "#{nombre1} + #{nombre2} = #{nombre1 + nombre2}"
| puts "#{nombre1} - #{nombre2} = #{nombre1 - nombre2}" 
| puts "#{nombre1} * #{nombre2} = #{nombre1 * nombre2}"
| puts "#{nombre1} / #{nombre2} = #{nombre1 / nombre2}" 
| ```