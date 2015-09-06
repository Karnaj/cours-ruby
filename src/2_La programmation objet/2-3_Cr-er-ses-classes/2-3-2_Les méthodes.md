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


# La méthode `initialize`

# Des méthodes d'accès aux variables
