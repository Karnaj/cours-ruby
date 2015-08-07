# Accéder à un élément

Les tableaux et tout c'est bien joli, mais pour le moment, on ne peut pas accéder à un élément du tableau. Comment faire ? Ne vous moquez pas, il faut encore utiliser les crochets `[]`. Pour accéder à l'élément d'indice $2$ du tableau `tab`, il nous faut juste écrire `tab[2]`. Voyons cela avec un exemple :

```ruby
grammaire = ["mais", "où", "et", "donc", "or", "ni", "car" ]
print grammaire[2]
```

Ce code permet d'afficher la chaine de caractère « et ».

[[attention]]
| À tous ceux qui pensaient que ce code afficherait « où » : n'oubliez pas, le premier indice d'un tableau 
| est l'indice $0$. L'élément d'indice $n$ est donc l'élément $n + 1$ du tableau.

Nous pouvons maintenant extraire n'importe quel élément d'un tableau. Cependant, lorsque que nous accédons à un élément du tableau, il faut faire attention qu'il y a bien un élément qui correspond à l'indice demandé. L'élément d'indice $5$ d'un tableau de taille $3$ n'existe pas. Contrairement à d'autres langages, Ruby ne provoque pas d'erreurs et retourne `nil` lorsque cela est fait, mais cela ne veut pas dire qu'il faut le faire.

On peut même afficher une partie du tableau seulement en utilisant les intervalles vus dans le chapitre précédent. Ils nous permettent d'obtenir un sous-tableau contenant tous les éléments du tableau dont les indices appartiennent à l'intervalle. 

```ruby
grammaire = ["mais", "où", "et", "donc", "or", "ni", "car"]
print grammaire[1..5]
```

Le code précédent affiche « ["où", "et", "donc", "or", "ni"] », c'est à dire les éléments dont l'indice est compris entre $1$ et $5$.
 
# Concaténation et ajout d'élément

La concaténation de tableau est l'ajout de deux tableaux. Cela permet de deviner de suite comment effectuer la concaténation. Oui, la concaténation de tableau se fait avec l'opérateur `+`. Son utilisation nous est maintenant normale :

```ruby
tab = [1, 2, 3]
tab = tab + [4, 5, 6]
print tab
```

Vous vous en doutez, avec ce code on obtient  « $[1, 2, 3, 4, 5, 6]$ ». Pas compliqué, non ?

Pour concaténer plusieurs fois le même tableau on utilise l'opérateur `*`. Pour avoir trois fois $[1, 2, 3]$, on utilise ce code :

```ruby
tab = [1, 2, 3]
tab = tab * 3
print tab
```
 
L'ajout d'éléments dans un tableau est un peu plus subtil. Une manière de voir les choses est de se dire que rajouter un élément à un tableau, c'est concaténer deux tableaux, l'un des tableaux n'ayant qu'un seul élément. 

Rajoutons l'élément $7$ à notre tableau `tab` :

```ruby
tab = [1, 2, 3, 4, 5, 6]
tab + [7]
print tab
``` 

On obtient « $[1, 2, 3, 4, 5, 6, 7]$ » comme prévu. L'autre méthode, à privilégier, est d'utiliser l'opérateur `<<`. Il modifie directement le tableau, ce n'est donc pas la peine de récupérer le résultat de l'opération.

[[attention]]
| L'opérateur `<<` ajoute au tableau l'élément qui est à droite contrairement à l'opérateur `+` qui 
| concatène les deux tableaux.

Ainsi, `tab << [3]` est différent de `tab + [3]`. Dans le premier cas, on ajoute au tableau un élément qui est un tableau, dans le second cas, on concatène deux tableaux, donc l'élément qui est ajouté au premier tableau est $3$ et non $[3]$. Regardez :

```ruby
tab1 = [1, 2]
tab2 = [1, 2]
tab1 << [3]
tab2 = tab2 + [3]
print "#{tab1} \n#{tab2}"
``` 

Avec ce code, on obtient :

```
[1, 2, [3]]
[1, 2, 3]
```
 
Cela signifie que pour ajouter un élément au tableau avec `<<`, il faut utiliser la syntaxe `tab << élément ` syntaxe qui ne marche pas avec l'opérateur `+` car cela signifierait additionner un tableau et un entier par exemple. Pour rajouter $3$ à notre tableau précédent, il fallait écrire `tab << 3`.

## Ajouter un élément à un indice précis

Nous avons un tableau de $3$ cases. Et nous voulons ajouter un élément à la sixième case du tableau. Pour cela, nous allons utiliser les crochets (très utiles ceux-là) :

```ruby
tab = [1, 2, 3]
tab[5] = 6
print tab
```  

Ce code affiche « $[1, 2, 3,$ nil, nil $, 5]$ » : la case qu'on voulait remplir a pris la bonne valeur et toutes les cases qui n'existaient pas ont pris la valeur `nil`. 

# Parcourir le tableau

Maintenant que nous savons comment accéder à chaque élément d'un tableau, vous pouvez envisager de parcourir le tableau en entier et de par exemple faire une même opération sur tous les éléments du tableau. Pour cela, il suffit d'utiliser une boucle `for`. Nous avons en effet dit qu'un tableau était une séquence, nous pouvons donc parcourir le tableau de la même manière que nous avons parcouru les intervalles.

Prenons l'exemple d'un menu de restaurant :

```ruby
menu_viande = ["un steak haché", "une entrecôte", "un rôti", "un faux-filet"]
for m in menu_viande
   print "Voulez-vous #{m} pour le diner de ce soir ?\n"
end
```
Tout d'abord, nous déclarons le tableau `menu_viande`. Ensuite nous parcourons notre tableau, la boucle `for` permet de répéter les instructions pour chaque élément du tableau. On obtient donc :

```
Voulez-vous un steak haché pour le diner de ce soir ?
Voulez-vous une entrecôte pour le diner de ce soir ?
Voulez-vous un rôti pour le diner de ce soir ?
Voulez-vous un faux-filet pour le diner de ce soir ?
```

En réfléchissant bien, on peut trouver une autre manière de faire cela en jouant avec les indices :

```ruby
menu_viande = ["un steak haché", "une entrecôte", "un rôti", "un faux-filet"]
for i in 0..3
   print "Voulez-vous #{menu_viande[i]} pour le diner de ce soir ?\n"
end
```

On incrémente cette fois la variable `i` à chaque tour de boucle et dans la boucle on affiche l'élément du tableau d'indice `i`.

Cela nous fait deux façons de parcourir le tableau. La première est plus lisible. Cependant ce n'est pas celle que nous utiliserons.

## La méthode `each`

C'est la méthode `each` que nous utiliserons. Elle sert à appliquer un bloc de code à chaque élément d'un tableau. Gardons l'exemple d'un menu de restaurant :

```ruby
menu_viande = ["un steak haché", "une entrecôte", "un rôti", "un faux-filet"]
menu_viande.each do |m|
   print "Voulez-vous #{m} pour le diner de ce soir ?"
end
```

Tout d'abord, nous déclarons le tableau `menu_viande`. Ensuite nous parcourons notre tableau, `do` répète les instructions pour chaque élément du tableau. On obtient le même résultat que précédemment.