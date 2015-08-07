Comme vous pouvez vous en douter, les tableaux sont des bel et bien des objets. Vous les avez déjà manipulé au début du cours sans même vous douter que tout ceci n'était qu'un survol des possibilités offertes par les tableaux. En guise de présentation, nous allons créer des tableaux de différentes manières :

```ruby
ary1 = [] # vous connaissez déjà cette notation
ary2 = Array.new # tiens ?
```

Voici une nouvelle notation tout à fait sympathique. Une faut savoir que les objets peuvent être créés en utilisant la méthode `new` de leur classe (à l'exception de quelques classes comme *Fixnum*, *TrueClass*, *NilClass*...). Dans le cas particulier de *Array* (la classe des tableaux), cette méthode peut être utilisée de plusieurs manières :

```ruby
ary1 = Array.new # toute nue, crée un tableau vide comme []
ary2 = Array.new(3) # crée un tableau de 3 cases rempli de nil, ici [nil, nil, nil]

# avec un bloc de code, chaque case du tableau sera initialisé grâce au bloc
# on obtient alors [0, 2, 4]
ary3 = Array.new(3) do |index|
  return index * 2
end
```

Comprenez bien que ces différentes utilisation de `new` sont spécifiques à *Array*, n'essayez pas ça avec d'autres classes qui ne sont pas prévues pour.