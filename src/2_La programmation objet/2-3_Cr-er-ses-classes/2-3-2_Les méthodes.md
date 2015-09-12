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

Il est maintenant temps de voir comment modifier les variables de nos objets. 

# La méthode `initialize`
