Nous allons maintenant écrire nos premières vraies fonctions. Certaines fonctions retournent une valeur particulière (la fonction `gets` par exemple retourne la chaîne de caractère rentrée par l'utilisateur). On peut donc demander à nos fonctions de retourner une valeur particulière, mais ce n'est pas obligatoire. Celles qui n'en renvoient pas renvoient `nil`. Ce sont ces fonctions que nous allons voir pour commencer.

# Procédure

Nous avons dit qu'une fonction qui ne retourne pas de valeur particulière retourne `nil`. On peut alors voir `nil` comme une valeur par défaut qui **signifie** qu'aucune valeur **réelle** n'est renvoyée (il faut comprendre que `nil` est renvoyée si le concepteur de la fonction n'a spécifié aucune valeur de retour). La fonction `print` par exemple renvoie `nil`. Pour voir cela, retournez sur `irb` et tapez `print` :

```
> print
=> nil
``` 

Une fonction qui retourne `nil` s'appelle une procédure. 
Prenons l'exemple d'une fonction qui affiche « Hello World » :

```ruby
#définition de la fonction 'bonjour'
def bonjour
    print "Hello World !"
end

bonjour #On appelle la fonction. Elle affiche "Hello World !"
```

Cette procédure ne fait qu'un bête affichage. Vous pouvez bien sûr changer cette affichage par ce que vous voulez et mettre autant d'instructions que vous le voulez dans votre fonction. 

Les procédures vous permettent d'éviter de devoir réécrire plusieurs fois des instructions identiques que vous utilisez souvent : vous écrivez une fois la procédure et vous l'appelez autant de fois que vous le voulez.

# Valeur de retour

Les procédures sont très utiles, mais une fonction qui renvoie quelque chose, c'est tout aussi bien. Pour étudier ce type de fonction, nous allons reprendre l'exemple du début de ce chapitre : nous allons écrire une fonction qui permet d'additionner deux nombres (nous l’appellerons `add`). Cette fonction devra retourner le résultat de l'addition. Voici comment cela se fait :

```ruby
#définition de la fonction 'add'
def add
   x = 9
   y = 5
   return x + y #retour
end

print add #nous devons utiliser 'print' pour afficher la valeur de retour
```

Vous avez vu comment nous retournons la valeur : avec le mot-clé `return`. `return x + y` permet donc de retourner la valeur de $x + y$. Dans cet exemple, `add` retourne `x + y`, soit `9 + 5`, et donc `14`. `print add` signifie affiche la valeur retournée par `add`, c'est à dire affiche $x + y$ et donc, ici, $14$. 

Le `return` n'est pas obligatoire. Nous aurions parfaitement pu écrire 

```ruby
def add  
   x = 9
   y = 5
   x + y #retour
end

print add
```

[[attention]]
| Le mot-clé return met fin à la fonction. Les instructions après le `return` ne seront pas exécutées.
  
Ainsi, dans ce code, le second `print` ne sera pas exécuté :

```ruby
def fonction
   print "Bonjour "
   return 0
   print "Merci." 
end
```

En fait, on peut utiliser `return` sans aucune valeur. Dans ce cas, aucune valeur ne sera retournée, le `return` servira juste à mettre fin à la fonction. On peut donc écrire ceci :

```ruby
def fonction
   print "Bonjour "
   return
   print "Merci." 
end
```

# Redéfinition de fonction

Quand on définit des fonctions, il faut faire attention. Si on définit plusieurs fois la même fonction, la version qui sera retenu quand on appellera la fonction sera la dernière que l'on aura définie. Ainsi, dans le code suivant, la fonction `bonjour` fera deux choses différentes. 

```ruby
def bonjour
   puts "Bonjour" 
   return 5
end

puts bonjour

def bonjour
   print "Bonjour utilisateur "
   return 10   
end

print bonjour
```

Le premier appel à `bonjour` affiche « Bonjour » et retourne $5$. Le second appel à `bonjour` affiche « Bonjour utilisateur » et retourne $10$. Finalement, ce code affiche :

```
Bonjour 
5
Bonjour utilisateur 10
``` 

Il faut donc faire attention à comment on définit nos fonctions. En fait, il vaut mieux ne jamais redéfinir une fonction et juste faire attention aux noms qu'on leur donne.