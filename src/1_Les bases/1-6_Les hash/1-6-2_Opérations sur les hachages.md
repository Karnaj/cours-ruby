# Accéder à un élément

Si vous vous rappelez bien, nous l'avons déjà fait dans la partie précédente. Comme pour les tableaux, il faut utiliser les crochets, et écrire entre eux la clé de l'élément auquel on veut accéder. Nos clés peuvent être tout et n'importe quoi, ne l'oubliez pas.

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}
print hachage["nom"]
```

Grâce à ce code, nous affichons la chaine `"Mon nom"`. 

Vous vous dites peut-être que nous sommes en train de radoter, mais ce n'est pas de notre faute si les tableaux et les hachages se ressemblent tant. En fait, ils se ressemblent tellement que même en essayant d'accéder à une valeur associée à une clé qui n'existe pas, on a la même réponse : 

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}
print hachage["Nom"]
```

Ce code affiche en effet `nil`, tout comme `print tab[5]` lorsque `tab` a plus de 6 cases.

[[attention]]
| Encore une fois on se répète, mais ce n'est pas parce que cet accès ne provoque pas d'erreur qu'on peut le
| faire. Essayez d'éviter toutes erreurs de ce type. 

# Ajout d'élément

Les opérateurs `+` et `<<`ne marchent pas avec les hachages. En fait, la seule manière de rajouter un élément est d'utiliser les crochets pour modifier un élément qui n'existe pas encore :

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}
hachage["autre"] = "nouveau"

print hachage
```

La clé `"autre"` n'existe pas encore, on lui assigne une valeur. 

[[question]]
| D'ailleurs, qu'est-ce qui se passe si on assigne deux fois une valeurs à la même clé lorsqu'on déclare un
| hachage ?

Faisons le test :

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015,
           "nom"    => "Mon nouveau nom"
}
print hachage
```

Et le résultat :

```
{"nom"=>"Mon nouveau nom", "prenom"=>"Mon prenom", "age"=>2015}
```

La valeur qui a été gardé pour la clé est la dernière que l'on avait associé. On ne peut donc associer qu'une seule valeur à une clé.

[[information]]
| Si vous avez par exemple fait du Python, les hachages de Ruby sont les dictionnaires de Python.

# Parcourir le hachage

Là on va arrêter de radoter ! Parcourir un hachage ne se fait pas du tout de la même manière que parcourir un tableau. Et c'est bien normal, on ne peut pas parcourir un hachage grâce aux indices puisqu'il n'y a pas d'indices. En fait, la seule méthode commune est celle qui consiste à parcourir directement le hachage avec `in` :

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}

for i in hachage 
   print i, "\n"
end
```
 
On déclare notre hachage et on le parcourt avec une boucle `for` pour obtenir au final 

```
["nom", "Mon nom"]
["prenom", "Mon prenom"]
["age", 2015]
```

Et là, nous sommes au regret de vous dire que tout comme pour les tableaux, nous n'allons pas utiliser cette technique, nous allons plutôt utiliser des méthodes.
  
## Parcourir les clés et les valeurs

Les hachages ont comme les tableaux une méthode `each`. Cependant, celle des hachages permet de parcourir les clés et les valeurs. Voyons un exemple :

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}

hachage.each do |cle, valeur|
    puts "La valeur #{valeur}  est associée à la clé #{cle}"
end
```

On parcourt tout le hachage en stockant chaque clé et chaque valeur dans les variables `cle` et `valeur`.

## Parcourir les valeurs

Avoir les valeurs et les clés c'est bien, mais ce serait bien de ne récupérer les valeurs. Pour cela, nous allons utiliser la méthode `each_value` :

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}

hachage.each_value do |valeur|
   puts "La valeur #{valeur} est dans le hachage"
end
```

Le code se passe de description. Vous devriez être capable de le comprendre tranquillement.

## Parcourir les clés

C'est plus rare de vouloir accéder aux clés d'un hachage, mais cela arrive. Heureusement, la méthode `each_key` est là pour nous aider à faire cela :

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}

hachage.each_key do |cle|
   puts "La clé #{cle} est une des clés du hachage"
end
```