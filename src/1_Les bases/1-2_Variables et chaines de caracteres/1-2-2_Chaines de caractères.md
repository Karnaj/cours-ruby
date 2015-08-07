Pour afficher une chaine de caractère (soit un mot ou une phrase), il faut l'entourer de guillemets simples ou doubles.

```ruby
> "Bonjour"
=> "Bonjour"
> 'Bonjour'
=> "Bonjour"
```

Pour déclarer une variable contenant une chaine de caractère, vous devez toujours utiliser le signe « = ». Il faut cependant faire attention à ne pas oublier les guillemets. De la même manière que pour les nombres, vous devez choisir un **identifiant** et lui assigner une valeur. De plus, vous pouvez également déclarer des chaines de caractères constantes, toujours en écrivant la première lettre de l'identifiant en majuscule.

```ruby
> mot = "zeste"
=> "zeste"
> Constante = "vrai"
=> "vrai"
```

Ici, la variable `mot` a alors pour valeur la chaine de caractères `zeste`.

# Opérations sur les chaines de caractères

Vous pouvez effectuer quelques opérations sur les chaines de caractères. Regardez :

```ruby
> "Bonjour " + "tout le monde"
=> "Bonjour tout le monde"
```

Cette opération s'appelle la **concaténation** (on dit qu'on **concatène** les deux chaines). Elle permet de mettre deux chaines bout à bout. Vous pouvez aussi insérer une variable dans une chaine de caractères grâce à la concaténation :

```ruby
> mot = "zeste"
=> "zeste"
> "Faites un " + mot + " envers votre prochain"
=> "Faites un zeste envers votre prochain"
```

Ici, nous avons concaténé trois chaines de caractères.

La concaténation se fait avec l'opérateur `+`. Si vous voulez obtenir plusieurs fois la même chaine, vous pouvez utiliser l'opérateur `*` :

```ruby
> mot = "zeste "
=> "zeste "
> mot * 3
=> "zeste zeste zeste "
```

La même chaine a été concaténé trois fois.

Une autre opération utile permet de rajouter une chaine à la fin d'une chaine de caractères. On peut aussi dire que c'est une concaténation. Cependant, le résultat de cette concaténation est directement affecté à la variable de départ.

```ruby
> mot = "zeste"
=> "zeste "
> mot << " de savoir"
=> "zeste de savoir"
```

La variable `mot` vaut alors `zeste de savoir`. Notez que cette concaténation ne s'utilise pas qu'avec des variables. Il est possible d'écrire `"zeste" << " de savoir"`.

[[information]]
| Tout comme pour les autres variables, vous pouvez récupérer le résultat de l'opération dans une variable. 

Ainsi :

```ruby
> mot = "zeste "
=> "zeste "
> repete = mot * 3
=> "zeste zeste zeste "
```

La variable répète vaut `zeste zeste zeste`.

Et pour que vous voyiez que l'on peut bien écrire `"zeste" << " de savoir"` :

```ruby
> mot = "zeste" << " de savoir"
=> "zeste de savoir"
```

On obtient alors la valeur `"zeste de savoir"` pour la variable `mot` sans étape intermédiaire.

Après la concaténation, parlons de l'interpolation de chaînes de caractères. Elle permet tout comme la concaténation de « rajouter des données dans une chaîne », mais s'avère parfois plus efficace. L'interpolation s'effectue de cette manière : on utilise « # » suivi de la variable entre parenthèses à l'endroit de la chaîne où nous voulons l'ajouter. Un exemple :

```ruby
> variable = "de savoir"
=> "de savoir"
> mot = "zeste #{de savoir}"
=> "zeste de savoir"
```

L'interpolation marche avec tous les types de variables que nous avons vu, pas seulement avec les chaînes de caractères. On peut même effectuer des calculs :

```ruby
> variable = 123 
=> 123
> "123 * 2 = #{variable * 2}"
=> "123 * 2 = 246"
> "123 + 2 = #{123 + 2}"
=> 123 + 2 = 125"
```

[[attention]]
| L'interpolation ne s'utilise qu'avec les guillemets doubles. Avec les guillemets simples, vous obtiendrez
|  « #{variable} ».

Si possible, utilisez toujours l'interpolation plutôt que la concaténation.