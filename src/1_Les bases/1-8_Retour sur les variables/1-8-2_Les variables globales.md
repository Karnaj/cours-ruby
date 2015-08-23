# Un problème : passage de variables aux fonctions

Nous allons maintenant nous intéresser à un problème : on passe une variable en paramètre à une fonction, comment faire pour que les modifications effectués sur la variable de la fonction affectent la variable que l'on a passé en argument. Un exemple de code pour voir le problème :

```ruby
def incrementer a =
   a = a + 1
end

x = 6
incrementer x 
print x 
```

On aimerait que la valeur de `x` soit `7` après l'appel de la fonction `incremente`, or elle a gardée son ancienne valeur `6`.

# Les variables globales

# Variables globales réservées
