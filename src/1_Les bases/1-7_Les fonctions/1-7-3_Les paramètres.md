Tout à l'heure, nous avons affiché « Bonjour » suivi de rien ou de « utilisateur » en redéfinissant la fonction. Nous allons maintenant voir la façon correcte de faire ceci grâce aux arguments des fonctions.

Les arguments sont des paramètres qui peuvent influer sur l'exécution d'une fonction. Les fonctions `print` et `puts` par exemple prennent en argument des données à afficher. En fonction des données passées, ce n'est pas la même chose qui est affiché. 

# Fonctions à un argument

Commençons par voir comment passer un argument à une fonction. Vous devez juste ajouter le nom que vous voulez donner à votre paramètre après le nom de la fonction. Vous pouvez le mettre entre parenthèse (ce n'est pas obligatoire, mais c'est conseillé). Voici le squelette d'une fonction avec argument :

```ruby
def nom_fonction(nom_argument)

end  
```

Vous pouvez alors utiliser l'argument dans votre fonction comme n'importe quelle autre variable. Ainsi, le bon code pour la fonction `bonjour` serait :

```ruby
def bonjour(nom)
   print "Bonjour #{nom}\n"
end

bonjour "utilisateur"
bonjour ""
``` 

On obtient alors :

```ruby
bonjour utilisateur
bonjour
```

Vous notez que l'on appelle alors la fonction en écrivant l'argument à côté (là encore, vous pouvez le mettre en parenthèses). Bien sûr, si vous n'appelez pas la fonction en lui passant le bon nombre d'arguments, vous aurez une erreur.

[[attention]]
| Les arguments ne peuvent pas être utilisés en dehors de la fonction. Ils sont définis uniquement dans la 
| fonction.

Ainsi, ce code provoquera une erreur :

```ruby
def bonjour(nom)
   print "Bonjour #{nom}\n"
end

bonjour "utilisateur"
bonjour ""

print nom
```

# Fonctions à plusieurs arguments

Les fonctions à plusieurs arguments ne sont pas plus compliqués à utiliser. La seule différence avec les fonctions à un argument est que vous devez utiliser une virgule pour séparer les arguments autant dans la définition de la fonction que dans son appel. Les règles à suivre restent les mêmes. Le squelette de la fonction devient alors :

```ruby
def nom_fontion(nom_argument1, nom_argument2, nom_argument3, nom_argument_n)

end  
```

Ce n'est vraiment pas plus compliqué que les fonctions à un argument.
 
Reprenons l'exemple de la fonction `add`. Les *arguments* permettent de définir la valeur de `x` et de `y` lors de l'appel de la fonction. Comme ceci :

```ruby
def add(x, y)
    return x + y
end

print add(4, 5) #nous affichons la valeur retournée par add(4, 5)
```

[[attention]]
| Là encore, le nombre d'arguments lors de l'appel doit être le même que lors de la définition de la 
| fonction. Dans notre cas, il n'y en que deux : `x` et `y`.

# Valeurs par défaut

Nous avons dit qu'il fallait passer le bon nombre d'arguments à la fonction lors de son appel. Néanmoins, ce serait bien de pouvoir se passer de certains arguments lors de certains appels, non ? Par exemple, pour notre fonction `bonjour`, de ne pas avoir à une chaîne vide en paramètre lorsque nous ne voulons pas afficher de nom. 

Nous sommes fiers de vous annoncer que vous pouvez faire tout cela en donnant à votre argument une valeur par défaut lorsque vous définissez votre fonction. En faisant cela, lorsque nous appelleront la fonction sans lui donner cet argument, sa valeur sera la valeur par défaut.
  
Pour définir une fonction avec une valeur par défaut, il faut écrire l'argument dans la définition de la fonction en lui donnant déjà une valeur. Notre fonction `bonjour` se code alors :

```ruby
def bonjour nom = ""
   print "Bonjour #{nom}\n"
end

bonjour "utilisateur"
bonjour 
```

Nous obtenons bien le résultat attendu.

[[information]]
| Vous pouvez faire des fonctions avec plusieurs arguments facultatifs. Cependant, ces derniers doivent être
| les derniers paramètres de votre fonction.

Quand on y réfléchit, c'est logique. Si on crée une fonction comme ceci (`def fonction(argument1, argument2 = 10, argument3`), comment savoir à quoi correspond `12` dans cet appel : `fonction(3, 12)`. Ici, on devine qu'il correspond au troisième argument, mais dans d'autres cas, vous voyez bien que c'est impossible.

[[information]]
| Notez tout de même que vous pouvez choisir l'ordre dans lequel vous transmettez vos paramètres à une 
| fonction. Il faut dans ce cas préciser le nom de l'argument.

Regardez ce code par exemple :

```ruby
def bonjour(nom, prenom)
   print "Bonjour #{nom} #{prenom}\n"
end

bonjour("moi", "utilisateur")
bonjour(prenom = "utilisateur", nom = "moi")
``` 

L'argument `prenom` vaut `utilisateur` dans les deux cas et l'argument `nom` vaut `moi` dans les deux cas. Les deux appels à la fonction donnent donc le même résultat.