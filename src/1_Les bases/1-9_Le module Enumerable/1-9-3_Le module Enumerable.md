Maintenant, nous savons comment créer des modules. Cependant, la création de module n’est pas l’objet principal de ce chapitre. L’objet principal de ce chapitre est un module en particulier, le module `Enumerable`.

Comme son nom le suggère, ce module semble permettre *d'énumérer*. Mais il n'en n'est rien. En fait, ce module est destiné aux éléments qui savent déjà comment énumérer leur contenu. C'est le cas des tableaux, des hachages, des chaînes de caractères ou encore des intervalles.

Par exemple, nous savons parcourir un tableau grâce à la méthode `each`. Un petite piqûre de rappel :

```ruby
[1, 2, 3, 4, 5].each do |i|
  # ...
end
```

Et c'est justement cette méthode qui va servir au module `Enumerable`. Nous allons voir que cette seule méthode permet de faire des tas de choses ! Il sufit de voir [la liste des fonctionnalités du module](http://ruby-doc.org/core-2.2.2/Enumerable.html). Grâce à lui, nous pouvons faire des opérations de recherche, de tri, de comptage, etc. Par exemple, il nous permet de connaître les éléments d’un tableau qui satisfont une condition.

[[info]]
| Dans la suite, nous traiterons uniquement des tableaux. Mais ce que nous verrons sera aussi valable pour les hachages, pour les chaines de caractères ou encore pour les intervalles.


## La méthode `all?`

Cette méthode permet de vérifier si tout les éléments d'un tableau correspondent à un critaire donné.

``` ruby
enumerable = [1, 2, 3]

is_even = enumerable.all? do |e|
	e.even?
end

is_even # => false
```

Ici nous testons la parité des éléments de notre tableau. Puisqu'ils ne sont pas tous pair, `all?` retourne `false`


Si rien n'est passé à la méthode, elle retourne `true` uniquement si tous les éléments du tableau sont évalués à `true`.
Autrement dit, si le tableau ne contient ni `false`, ni `nil`, `all?` retourne `true`

``` ruby
[1, nil].all? # => false
[5, "salut"].all? # => true
```

## La méthode `none?`

 Cette méthode est la complémentaire de `all?`. Elle renvoie `true` si aucun élément ne satisfait le critère donné.
 
``` ruby
enumerable = [1, 2, 3]

enumerable.none? { |e| e.even? } # => false 
enumerable.none? { |e| e > 5 } # => true 
``` 

Si rien n'est passé à la méthode, elle retourne vrai uniquement si le tableau ne contient que `false` ou `nil`

``` ruby
[false, nil].none? # => true
[true, nil].none? # => false
```


## La méthode `any?`

Cette méthode ressemble beaucoup à `all?`, à la différence que celle ci retourne `true` si *au moins un* élément correspond au critère.
Autrement dit, cette méthode retourne `false` si aucun élément ne correspond au critère.

``` ruby
enumerable = [1, 2, 3]

is_even = enumerable.all? do |e|
	e.even?
end

is_even # => true
```

Puisque **2** est pair, le critère est validé.

## La méthode `one?`

Cette méthode est le complémentaire de `any?`. Elle retourne `true` si un, et seulement un, élément est égal à celui passé en paramètre.
Si la méthode ne reçoit aucun paramètre, alors elle retourne `vrai` si un seul élément est évalué à `true`.

``` ruby
enumerable = [1, 2, 3]

enumerable.one? # => false
enumerable.one?(1) # => true


enumerable2 = [1, 1, true]

enumerable2.one? # => false (car 1 est évalué à vrai)
enumerable2.one?(1) # => false

[false, nil, true].one? # => true
```


## La méthode `collect`

Cette méthode permet d'effectuer un traitement à tous les éléments d'un tableau, et de retourner tous les résultats dans un tableau.
`map` est un alias de `collect` (les deux sont équivalents).

``` ruby
enumerable = [1, 2, 3]

res = enumerable.collect do |e|
  e + 1
end

res # => [2, 3, 4]
```

C'est simple comme bonjour, et très pratique !


## La méthode `count`

Certainement la méthode la plus simple. Elle retourne la taille du tableau.

``` ruby
enumerable = [1, 2, 3]

enumerable.count # => 3
```

Elle permet aussi de compter le nombre d'éléments satisfiant un critère donné.

``` ruby
enumerable = [1, 2, 3]

n = enumerable.count do |e|
  e.odd?
end

n # => 2
```

En effet, **1** et **3** sont impairs, donc le nombre d'éléments impair est bien **2**.

## La méthode `find`

Cette méthode permet de chercher le premier élément satisfiant un critère donné.
`detect` est un alias de `find` (les deux sont équivalents).

``` ruby
enumerable = [1, 2, 3]

n = enumerable.find do |e|
  e.odd?
end

# Equivalent à
# n = enumerable.detect do |e|
#   e.odd?
# end

n # => 1
```

## La méthode `find_all`

Cette fois ci, cette méthode retourne tous les éléments satisfiant un critère.
Attention, il n'existe pas d'alias `detect_all` ! Cependant, il existe un alias `select`.

``` ruby
enumerable = [1, 2, 3]

n = enumerable.find_all do |e|
  e.odd?
end

# Equivalent à
# n = enumerable.select do |e|
#   e.odd?
# end

n # => [1, 3]
```

## La méthode `first`

Cette méthode retourne le premier élément du tableau.

``` ruby
enumerable = [1, 2, 3]
enumerable.first # => 1
```

Elle peut aussi retounrer les *n* premiers éléments.

``` ruby
enumerable = [1, 2, 3]
enumerable.first(2) # => [1, 2]
```

## La méthode `include?`

Cette méthode retourne `true` si la valeur passé en paramètre est présente dans le tableau.

``` ruby
enumerable = [1, 2, 3]
enumerable.include?(2) # => true
enumerable.include?(5) # => false
```

## La méthode `inject`

Cette méthode permet de faire une opération dite de *réduction*.
`reduce` est un alias de cette méthode.

``` ruby
enumerable = [1, 2, 3]

## Différentes façon de calculer une somme

sum = enumerable.inject(:+)

# Ici, acc est un accumulateur, il vaudra successivement 1, 3 puis 6
sum = enumerable.inject { |acc, e| acc + e }
# La ligne au dessus correspond à :
acc = 0
enumerable.each { |e| acc = acc + e }


## Différentes façon de calculer un produit

product = enumerable.reduce(1, :*) # On doit specifier la valeur de base de l'accumulateur (0 par défaut)

product = enumerable(1) { |acc, e| e * acc }


## Recherche de la plus longue chaine
longest = %w{ cat sheep bear }.inject do |memo, word|
   memo.length > word.length ? memo : word
end
longest # => "sheep"
```

Dans le dernier exemple, l'accumulateur sert à mémoriser le plus long mot parcouru jusq'ici.

Ces exemples sont tirés de la documentation du module `Enumerable`


## Les méthodes `max` et `min` et `minmax`

Ces méthodes retournent respectivement le maximum d'un tableau, le minimum, un tableau contenant le minimum et le maximum

``` ruby
enumerable = [1, 2, 3]

enumerable.max # => 3
enumerable.max(2) # => [2, 3]

enumerable.min # => 1

enumerable.minmax # => [1, 3]
```

## La méthode `reject`

Cette méthode retourne la liste des éléments ne satisfiant pas un critère donné.
Elle fait le contraire de ce que fait `select` (alias `find_all`)

``` ruby
enumerable = [1, 2, 3]

enumerable.reject { |e| e.even? } # => [1, 3]
```


## La méthode `reverse_each`

Cette méthode parcours le tableau à l'envers.

``` ruby
enumerable = [1, 2, 3]

enumerable.reverse_each do |e|
  puts e
end

# Affiche
# 3
# 2
# 1
```

[[attention]]
| Cette méthode créer un tableau temporaire contenant les éléments du tableau initial, mais dans le sens inverse.

Cette méthode peut donc être assez lourde sur de gros tableau. Cette méthode illustre bien la façon dont les méthodes du module `Enumerable` 
fonctionnent : elles ne font appelle qu'à `each`, or ce dernier renvoit les éléments dans le bon ordre, c'est pour cela qu'un tableau 
temporaire inversé est nescessaire.

## La méthode `sort`

Cette méthode trie simplement un tableau.

``` ruby
enumerable = [2, 3, 5, 4]

enumerable.sort # => [1, 2, 3, 4]
enumerable.sort { |a, b| a <=> b } # => [1, 2, 3, 4]
enumerable.sort { |a, b| b <=> a } # => [4, 3, 2, 1]
```

## La méthode `sort_by`

Cette méthode trie un tableau selon les attributs de ses éléments.

``` ruby
enumerable = %w( poire abricot cerise )

enumerable.sort_by { |e| e.size } # => ["poire", "cerise", "abricot"]
```

En fait, on peut trier selon n'importe quoi

``` ruby
enumerable = [1, 2, 3, 4, 5, 5, 7, 8, 9]

enumerable.sort_by { |e| Random.rand(10) }
```

Ce qui nous génère un tableau trié aléatoirement. 
Cependant, pour trier un tableau aléatoirement, la méthode `shuffle` est bien meilleure (elle ne fait pas partie de `Enumerable`).

## La méthode `to_a`

Cette méthode retourne un enumerable sous forme de tableau.
`to_a` signifie *to array*

``` ruby
[1, 2, 3].to_a # => [1, 2, 3]
(1..3).to_a # => [1, 2, 3]
{ a: 1, b: 2}.to_a # => [[:a, 1], [:b, 2]]
```
