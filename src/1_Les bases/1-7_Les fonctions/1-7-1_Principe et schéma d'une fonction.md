# Qu'est-ce qu'une fonction

Une fonction est un ensemble d'instructions permettant de réaliser une certaine tâche (additionner deux nombres par exemple). Vous pouvez créer des fonctions pour faire tout et n'importe quoi. Si vous voulez faire une fonction qui `répéterMessage` qui affiche un message $10$ fois, vous pouvez. Les fonctions `puts` et `print` affichent des messages par exemple.

Lorsque vous utilisez une fonction dans un programme, on dit que l'on appelle cette fonction. Tout comme vous pouvez utiliser `print`  autant de fois que vous le voulez, vous pouvez appeler n'importe quelle fonction autant de fois que vous le voulez dans votre programme. 

Les fonctions permettent de n'écrire le code qu'une seule fois. Imaginez que vous avez un code de $20$ lignes qui fait une action, et que vous faîtes cette même action à $3$ endroits différents de votre programme. Plutôt que de recopier le code à chaque fois, vous allez faire une fonction qui effectue cette action et l'appeler à chaque fois. Ainsi, plutôt que d'écrire $60$ lignes, vous allez écrire $23$ lignes, $20$ lignes pour la fonction, et $1$ lignes par appel à la fonction (en fait ça fera $25$ lignes). 

On peut donc voir les fonctions comme des sous-programmes. Elles permettent de rendre le programme plus *modulable*.  

# Déclarer une fonction

Voyons maintenant comment déclarer une fonction en Ruby. Voici le schéma d'une fonction :

```ruby
#définition de la fonction 'add'
def add
    #instructions
end
```

La définition d'une fonction débute par le mot-clé `def` et se termine par `end`. Ici, nous avons déclaré a fonction `add`. Une fois qu'une fonction est déclarée, vous pouvez l'appeler dans votre programme comme n'importe quelle autre fonction. Par exemple, on pourrait appeler la fonction `add` de cette manière :

```ruby
print "J'appelle la fonction add : " 
add
print "C'est fait"
```
 
Bien sûr, si une fonction n'est pas définie, vous ne pouvez l'appeler et vous obtiendrez une erreur. Ainsi, ce code ne fonctionnera pas :

```ruby
a = 4
b = 5
bonjour
```

Le code qui va suivre est par contre parfaitement valable. La fonction `bonjour`, même si elle ne fait rien du tout y est définie :

```ruby
def bonjour
    #instructions
end

a = 4
b = 5
bonjour
```

[[attention]]
| Une fonction doit être définie avant son utilisation.

Ainsi, ce code ne fonctionne pas :

```ruby
a = 4
b = 5
bonjour

def bonjour
    #instructions
end
``` 

On pourrait pourtant penser que ce code est le même que le précédent. Cependant quand l'interpréteur arrive à `bonjour`, il ne connaît pas encore `bonjour`, et donc on obtient une erreur.

[[information]]
| En Ruby, il est conseillé d'écrire les noms des fonctions en conventions 
| [snake_case](https://fr.wikipedia.org/wiki/Snake_case) (comme les noms de variables).