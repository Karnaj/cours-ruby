La boucle `while` st une structure de boucle plutôt simple. Elle permet de répéter des instruction tant qu'une condition est vraie. Encore une fois, remarquez que `while` est l'équivalent anglais de `tant que`.

Prenons le cas d'un programme qui affiche la table de multiplication d'un nombre. Il affiche les produits de ce nombre par les entiers de $1$ à $10$ :

```ruby
n = 1
while n <= 10 # tant que n est inférieur ou égal à 10, le code est exécuté
   print "#{n * 8}"
   n = n + 1 # on rajoute 1 à n à chaque tour pour que sa valeur atteigne 10
end
```

Ici, nous affichons la table de $8$. Pour cela, nous initialisons une variable à $1$. Cette variable s'appelle un **compteur**. Tant que cette variable sera inférieur ou égal à $10$, on affichera le résultat du produit de $8$ et de cette variable, puis on ajoutera à cette variable $1$ (on dit qu'on **incrémente** la variable).  

[[attention]]
| Là encore, le mot-clé `end` est obligatoire.

Exécutez le programme et voyez le résultat :

```bash
8 16 24 32 40 48 56 64 72 80
```

La structure d'une boucle `while` est vraiment très proche de celle d'un `if`. On pourrait presque se dire que c'est un `if` qui se répète tant que la condition est vraie. 

D'ailleurs, vous pouvez aussi utiliser une forme condensée de `while`. On pourrait alors écrire le programme précédent de cette manière :

```ruby
n = 1

(print "#{n * 8} "; n = n + 1) while n <= 10
```

Tout comme pour le `if` et sa forme condensée, la plupart du temps, préférez le `while` classique à sa forme condensée.

# La structure `begin - while`

Il peut arriver que vous vouliez qu'une instruction se répète en fonction d'une condition (donc une boucle `while`) , mais que vous vouliez également que cette instruction soit exécutée au moins un fois. Vous pouvez vous dire qu'il suffit de placer l'instruction une fois avant la boucle, et une autre fois dans la boucle.  

La structure `begin...end while` équivaut à un `while`, sauf que le code est exécuté au moins une fois. Avec cette structure, le `while` se retrouve à la toute fin de la boucle. Reprenons l'exemple précédent en utilisant cette structure : 

```ruby
n = 1
begin
   print "#{n * 8} "
   n = n + 1
end while n <= 10
```

Cet exemple c'est peut-être pas très parlant. Regardez alors celui-là :

```ruby
n = 6

begin 
   print "n " 
end while n < 5
```

La condition n'est même pas vraie au premier tour de boucle, mais les instructions sont toujours exécutées au moins une fois. En fait, la condition n'est évaluée qu'après le premier tour de boucle et ceci car elle est évaluée après l'exécution des instructions (le `while` est à la fin pour cette raison).

[[attention]]
| Encore une fois, le `end` est obligatoire, et là, il est à placer **avant** le while qui se retrouve alors 
| à la fin de la boucle.

En dehors de ceci, la structure `begin - while` fonctionne exactement comme la structure `while`. Il faut cependant faire attention à la forme condensée et ne pas oublier d'y intégrer le `end` de cette manière :

```ruby
n = 11

begin (print "#{n * 8} "; n = n + 1) end while n <= 10
```  

# La structure `until`

Rendons à César ce qui est à César : la boucle `until` est à la boucle `while` exactement ce que la condition `unless` est à la condition `if`. Ainsi, la boucle `until` est une boucle qui s'exécute jusqu'à ce que la condition soit vraie, c'est à dire tant qu'elle est fausse. On a donc `until(condtition)` qui est équivalent à `while!(condition)`. Réécrivons le programme précédent avec une boucle `until` :

```ruby
n = 1
until n > 10 # jusqu'à ce que n soit plus grand que 10, le code est exécuté
   print "#{n * 8} "
   n = n + 1 
end   
```

Vous remarquerez que l'inégalité stricte que l'on avait avec la boucle `while` devient large avec la boucle `until`. En efet, on veut s'arrêter quand $n$ sera strictement supérieur à $10$.

Encore une fois, et vous vous en doutiez sûrement, nous pouvons utiliser la structure condensée :

```ruby
n = 1

(print "#{n * 8} "; n = n + 1) until n > 10
```