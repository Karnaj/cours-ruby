# Un problème : passage de variables aux fonctions

Nous allons maintenant nous intéresser à un problème : on passe une variable en paramètre à une fonction, comment faire pour que les modifications effectués sur la variable de la fonction affectent la variable que l'on a passé en argument. Un exemple de code pour voir le problème :

```ruby
def incrementer(a) =
   a = a + 1
end

x = 6
incrementer x 
print x 
```

On aimerait que la valeur de `x` soit `7` après l'appel de la fonction `incremente`, or elle a gardée son ancienne valeur `6`. 

On pourrait alors se dire que c'est normal, qu'il suffit d'incrémenter `x` plutôt que `a` dans la fonction `incrementer` (et dans ce cas, l'arguement n'est plus nécessaire).

```ruby
def incrementer
   x = x + 1
end

x = 6
incrementer x 
print x 
```

Et ce code ne fonctionne pas, et nous obtenons une erreur. Cette erreur est due à ce que l'on appelle la **portée des variables**. Il s'agit de définir dans quelle partie du code une variable existe. Il faut donc savoir que les variables n'existent que dans le bloc dans lequel elles ont été déclarées. Ainsi, dans notre code précédent, les deux variables `x` sont différentes :

- la variable `x` de la fonction `incrementer` n'existe que dans la fonction `incrementer` et pas en dehors ;
- la variable `x` du reste du code n'existe qu'en dehors de la fonction `incrementer`.

On dit que ce sont des variables **locales**.

Ainsi, dans la fonction `incrementer`, on essaie d'incrémenter la valeur de `x`, or `x` n'existe pas encore (et a donc la valeur `nil`) et l'opération `nil + 1` ne peut pas être faite.

Pour mieux voir le phénomène de portée, testez des codes de ce genre :

```ruby
def f(x)
   x = x + 1 # Fonctionne car x existe étant un paramètre
   puts x
end

def g
   x = 3 # On est obligé de déclarer x avant 
   x = x + 1
   puts x
end

def h(x)
   x = x + 1 
   puts x 
   return x # On retourne x
end

x = 1
f x
puts x # x vaut toujours 1 en dehors de la fonction
g x
puts x # x vaut toujours 1 
h x
puts x # x vaut toujours 1
x = h x 
puts x # x vaut maintenant 2 car on a récupérer la valeur retourner par la fonction h
```

Ce code nous montre qu'il est possible de faire la fonction incrémenter grâce au retour de la fonction (nous le savions déjà). Mais si notre fonction doit changer plusieurs valeurs, c'est déjà plus embêtant à faire.

# Les variables globales

Pour régler ce problème, nous pouvons utiliser une variable globale. Les variables globales sont des variables qui, contrairement aux variables locales, sont accessibles dans tout le programme. Pour déclarer une variable globale, il suffit de préfixer son nom du caractère `$`.

```ruby
$x # x est une variable globale
```

[[attention]]
| Les variables `x` et `$x` sont bien sûr différentes.

Ce code fonctionne donc :

```ruby
def afficher =
   print $x
end

$x = "Voici une variable globale"
afficher
```

Nous sommes maintenant capable de faire une fonction qui incrémente la variable globale `$x` :

```ruby
def incrementer 
   $x = $x + 1
end

$x = 1
incrementer
print $x #affiche 2
```

Les variables globales vous semblent être une solution pertinente aux problèmes que vous pourrez avoir, et vous pensez sûrement à les utiliser tout le temps. Pourtant, leur utilisation peut s'avérer dangereuse et ne conduit pas à une bonne conception de programme. On peut presque toujours se passer des variables globales et c'est ce que nous ferons.

# Variables globales réservées

Il existe des variables globales dont le nom est réservé. Cela veut dire que vous ne pourrez pas utiliser ces noms de variables dans votre programme. Ces variables ont chacune leur utilité et nous pouvons utiliser les dans nos programmes. Voyons en quelques unes :
