Maintenant que nous savons créer des tableaux en bonne et due forme, il est temps d'apprendre à s'en servir. Afin de commencer les hostilités, nous allons voir quelques méthodes qui permettent de manipuler chaque élément de notre tableau :

- `each` : permet d'exécuter un bloc de code pour chaque élément du tableau
- `each_index` : pareil que `each` mais envoie l'indice de l'élément dans le tableau comme paramètre du bloc
- `collect` et `map` : d'exécute un bloc de code pour chaque élément du tableau et crée un tableau avec le résultat de chaque exécution
- `delete_if` : Supprime tous les éléments du tableau pour lesquels l'exécution du bloc a renvoyé *True*
- `keep_if` : Ne garde que les éléments du tableau pour lesquels l'exécution du bloc a renvoyé *True*
- `shuffle` : Mélange le tableau

Voici quelques exemples d'utilisation de ces méthodes :

```ruby
# en Ruby, le return est optionnel
# en cas d'absence, le résultat de la dernière instruction évaluée est retourné
ary = Array.new(3) { |i| i * 2 }
ary.each { |elem| print elem } # affiche tous les éléments de ary
ary.collect { |elem| elem + 1 } # renvoie [1, 3, 5]
ary.keep_if { |elem| elem > 1} # renvoie [2, 4] et modifie ary !
```

Il existe une version des méthodes `map`, `shuffle`, `collect`, `sort` (qui permet de trier le tableau) qui modifient directement le tableau plutôt que d'en créer un nouveau. Il suffit alors de rajouter un `!` à la fin du nom de la méthode :

```ruby
ary = Array.new(3) { |i| i * 2 } # [0, 2, 4]

# Ces deux lignes sont équivalentes !
ary = ary.collect { |elem| elem + 1 }
ary.collect! { |elem| elem + 1 } # Le ! fait partie du nom de la méthode, pas d'espace entre collect et !
```

-----------

Petit exercice d'application :
------------------------------

- Créez un tableau appelé **ary** qui contient les 10 premiers entiers naturels (donc de 0 à 9) grâce à la méthode `new` suivie d'un bloc.
- Ne gardez que les nombres pairs et mélangez ce tableau.
- Affichez tous les éléments de ce tableau.

Vous devez tout faire dans le même tableau !

Correction :
------------

[[secret]]
| ```ruby
| ary = Array.new(10) { |i| i } # utilise l'indice comme valeur pour chaque élément
|
| # Si le reste de la division euclienne par 2 donne 0, le nombre est pair
| ary.keep_if { |elem| elem % 2 == 0 }
| ary.shuffle!
|
| ary.each { |elem| puts elem } # puts affiche elem et effectue un retour à la ligne
| ```