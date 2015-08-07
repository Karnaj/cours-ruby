La structure `if - else` est la plus simple des structures conditionnelles. On évalue une expression (on regarde si elle vaut `true` ou `false`), si (`if`) elle vaut `true`, on exécute certaines instructions, sinon (`else`) on en exécute d'autres.

Prenons le cas d'un programme qui demande l'âge de l'utilisateur et nous dit s'il est majeur ou mineur. S'il a moins de 18 ans, il est mineur, sinon il est majeur :

```ruby
age = gets.chomp.to_i #On récupère une saisie et on la convertit en entier

if age < 18
   print "Vous êtes mineur"
else #sinon
   print "Vous êtes majeur"
end
```

Ici, nous vérifions si la variable `age` est inférieur à 18 grâce à `<`. Essayez de rentrer des âges inférieurs ou supérieurs à 18 et admirez le travail :magicien: .  

L'[indentation](http://fr.wikipedia.org/wiki/Style_d%27indentation) n'est pas obligatoire comme en Python. 
Cependant, il faut quelque chose pour séparer le `if condition` des instructions à exécuter. Le retour à la ligne est l'un des moyens de faire cette séparation. Le mot clé `then` (alors) est l'autre manière de la faire. Utiliser `then` suivi d'un retour à la ligne peut être très utile pour la lisibilité. 

[[attention]]
| Cette structure conditionnelle se termine toujours par le mot-clé `end`. C'est très important, ne 
| l'oubliez pas.

Le `else` n'est pas obligatoire. Vous pouvez parfaitement écrire :

```ruby
age = gets.chomp.to_i #On récupère une saisie et on la convertit en entier

if age < 18 then
   print "Vous êtes mineur"
end
``` 

# Le mot-clé `elsif`

Si vous n'avez pas seulement deux possibilités, vous pouvez compléter votre structure `if-else` avec un `elsif` (sinon si). Il permet d'ajouter une autre possibilité à la condition `if`. Prenons le code précédent et rajoutons un `elsif` :

```ruby
age = gets.chomp.to_i

if age < 18 #si age est inférieur à 18
   print "Vous êtes mineur"
elsif age > 80 #si age est supérieur à 80
   print "Vous êtes senior"
else #sinon
   print "Vous êtes majeur et votre âge est inférieur à 80 ans"
end
```

On regarde si la première condition est vraie. Si elle vraie, on affiche que l'utilisateur est mineur, sinon on regarde la seconde condition et enfin on arrive au `else` qui s'exécute si aucune des conditions précédentes n'est vraie.

[[information]]
| Vous pouvez utiliser autant de `elsif` que vous voulez.

Ce n'est vraiment pas compliqué à utiliser. La seule subtilité est que les remarques que nous avons tenues à propos du `if` sont aussi valables pour le `elsif` : là encore, vous devez utiliser `then` sans quoi le retour à la ligne est obligatoire.

Notez qu'il existe une façon plus concise d'écrire un `if` :

```ruby
age = gets.chomp.to_i

print "Vous êtes majeur" if age >= 18 
```

Dans ce cas, il n'y a pas de `end` et l'instruction à exécuter doit être unique. Cependant, vous pouvez placer plusieurs instructions en utilisant le point-virgule et des parenthèses de cette manière :

```ruby
age = gets.chomp.to_i

(print "Vous êtes majeur."; print "Peut-être même que vous êtes sénior.") if age >= 18 
```
 
N'abusez pas de cette notation. Elle peut-être utilisée dans les cas où il n'y a **vraiment** qu'une seule instruction à exécuter, mais même là, si la condition -- ou même l'instruction -- est trop compliquée, privilégiez un `if` classique.
 
# La structure `unless`

La structure `unless` fonctionne exactement de la même manière que `if` et est en fait la condition contraire de `if`. Avec `unless`, les instructions sont toujours exécutés **sauf** lorsque la condition est vérifiée. On a donc `unless (condition)` qui est équivalent à `if !(condition)`. Pour l'âge on peut donc écrire ce programme :

```ruby
age = 19

unless age < 18
   print "Vous êtes majeur"
else
   print "Vous êtes mineur"
end
```

Là encore, vous pouvez utiliser la structure condensée :

```ruby
print "Vous êtes majeur" unless age < 18 
```