# Créer les méthodes de la classe

Nous savons déjà comment créer des méthodes. Il est maintenant temps de voir comment créer des méthodes liées à un objet. Oui, oui, celles que nous utilisons avec  le signe `.`. Ces méthodes sont appelées **méthodes d'instance**. Pour les déclarer, il suffit de déclarer une méthode tout à fait normale dans une classe. Par exemple, complétons notre classe `Ordinateur` :

```ruby
class Ordinateur
   def allumer
      puts "Allumage en cours." 
   end
   
   def eteindre
      puts "Extinction en cours."
   end
end
```

Et donc, nous pouvons créer une instance d'`Ordinateur`, l'allumer, puis l'éteindre :

```ruby
a = Ordinateur.new
a.allumer
puts "Maintenant que nous avons allumé l'ordinateur, nous pouvons faire tout plein d'opérations."
a.eteindre
```

Vous savez alors commen faire des fonctions avec paramètres (facultatif ou non), qui retournent une valeur...

```ruby
class Ordinateur
   def allumer
      puts "Allumage en cours." 
   end
   
   def eteindre
      puts "Extinction en cours."
   end
   
   def bonjour(prenom = "le monde")
      puts "bonjour #{prenom}."
   end
end

a = Ordinateur.new
a.allumer
a.bonjour
a.bonjour "utilisateur"
a.eteindre
```

Les méthodes d'instances ne sont vraiment rien d'autres que des méthodes placées dans une classe. Une des seules chose que vous avez besoin de savoir en plus c'est comment appeler une méthode de la classe... Dans une autre méthode de la classe. Par exemple, faisons une fonction `quitter` de paramètre `prenom` qui dise au revoir à `prenom` et appelle ensuite la fonction `eteindre`. Essayons ceci :

```ruby
def quitter(prenom = "le monde")
   puts "Au revoir #{prenom}."
   eteindre
end
```

Et ça fonctionne. Cependant, la plupart du temps, nous allons utiliser le mot-clé `self` :

```ruby
def quitter(prenom = "le monde")
   puts "Au revoir #{prenom}."
   self.eteindre
end
```

Ce mot-clé permet de faire référence à l'objet qui appelle la méthode. Ainsi, lorsque nous utilisons `a.quitter`, dans la méthode `quitter`, `self.eteindre` équivaudra à `a.eteindre`.

# Des méthodes d'accès aux variables

Il est maintenant temps de voir comment modifier les variables de nos objets. Une première idée serait qu'on peut y accéder en utilisant le symbole `.` :

```ruby
class Ordinateur
   @h 
end

ordi = Ordinateur.new
ordi.h = 32 # Erreur
print ordi.h # Erreur également
```

[[erreur]]
| On ne peut pas accéder aux informations d'un objet de cette manière.

Cela est dû à ce que l'on appelle **l'encapsulation**. Il s'agit d'un principe en programmation orienté objet. Il consiste en gros à rassembler les données dans une structure (ce que nous faisons avec les objets) et à masquer ces données, en les rendant accessibles uniquement à l'intérieur de l'objet lui-même. Ainsi, nous ne pouvons pas avoir accès à la variable `h` de notre objet `ordi` **à l'extérieur** de notre classe. Il nous faut donc utiliser des méthodes **à l'intérieur** de notre classe qui se chargeront de renvoyer ou de modifier les variables. Par exemple :

```ruby
class Ordinateur
   @h
   
   def get_h 
      @h
   end
   
   def set_h valeur 
      @h = valeur
   end
end

ordi = Ordinateur.new
ordi.set_h 800
print "La hauteur de l'écran est #{ordi.get_h}"
```

Et là pas d'erreur, on obtient bien : 

```
La hauteur de l'écran 
```

Vous devez donc retenir que pour accéder aux variables de vos objets, il vous faut utiliser des classes. Notez que le chapitre suivant sera consacré à cela et vous permettra d'accéder à vos variables en écrivat moins de code et de façon plus efficace. 

# La méthode `initialize`

Posons nous une petite question sur la classe `Ordinateur` précédente : lorsque j'instancie un objet de cette classe, quelle est la valeur donnée à `h` ? Affichons la pour voir :


```ruby
class Ordinateur
   @h
   
   def get_h 
      @h
   end
   
   def set_h valeur 
      @h = valeur
   end
end

ordi = Ordinateur.new
print "La hauteur de l'écran est #{ordi.get_h}"
```

Résultat : aucun nombre n'est affiché. 

C'est quand même embêtant. On aimerait bien que lorsqu'un nouvel `Ordinateur`, il ait une hauteur par défaut, ou encore mieux on aimerait pouvoir lui donner une hauteur à sa création. En fait, on aimerait bien pouvoir faire automatiquement des opérations sur l'objet dès sa création. Pour ce faire, nous allons utiliser une méthode spéciale, la méthode `initialize`. Cette méthode permet de définir le comportement par défaut d'un objet à sa création. Elle est appelée dès que l'objet est créé. Il s'agit d'un **constructeur**. 

Utilisons donc cette méthode pour donner une valeur à nos variables et afficher un message informant qu'un objet de la classe `Ordinateur` est créé :

```ruby
class Ordinateur
   @h
   
   def initialize(h = 600)
      @h = h
      puts "Un ordinateur est créé."
   end
   
   def get_h 
      @h
   end
   
   def set_h valeur 
      @h = valeur
   end
end
```

Si on tape `ordi = Ordinateur.new`, un ordinateur avec `@h = 600` sera instancié et le message sera affiché. Si on tape `ordi = Ordinateur.new(h = 800)`, le message sera aussi affiché, mais on aura pour cet ordinateur `@h = 800`.

Nous voyons bien l'utilité de la méthode `initialize`.


