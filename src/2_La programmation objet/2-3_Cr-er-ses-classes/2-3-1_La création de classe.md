# Création de notre première classe

Nous sommes maintenant fin prêt à créer nos propres classes. Pour déclarer une classe, il faut procéder ainsi :

```ruby
class Ordinateur

end
```

Et oui, c'est le retour du mot-clé `end` ! Il permet de terminer la déclaration d'une classe, le mot-clé permettant de commencer cette déclaration étant `class`. Le `end` est donc encore très important, et l'oublier ne vous apportera rien de bon. 

Ici, nous avons déclaré une classe `Ordinateur`. Elle est vide, c'est à dire qu'elle ne contient aucune variable ni aucune méthode. La seule chose que l'on peut faire, c'est instancier des objets de cette classe :

```ruby
laptop = Ordinateur.new
```

En gros, rien de bien compliqué pour le moment. Mais avant de passer à la suite, retournons sur la déclaration de classes en elle-même.

[[question]]
| Tous les noms de classes que nous avons vu commencent par une majuscule, c'est une convention ou il y a une raison ?

Cela aurait pu être une convention pour distinguer les variables des classes. Mais ce n'est pas cela. Essayons de déclarer une classe avec un nom qui commence par une minuscule :

```ruby
class ordinateur

end
```

On obtient une erreur : `class/module name must be CONSTANT`. Elle est très claire, le nom doit être une constante (et donc commencer par une majuscule). Ce n'est donc pas une lubie de programmeur, **les noms de classes doivent obligatoirement commencer par une majuscule**.

Vous pourriez alors vous dire que si c'est une constante, tout le nom devrait être en majuscule (comme pour les noms de variables constantes), mais par convention cette fois, seule la première lettre prend une majuscule contrairement aux variables constantes. 

# Les variables

Il est maintenant temps de rajouter des variables à notre classe. Essayons donc de rajouter des variables à notre classe :

```ruby
class Ordinateur
   w = 800 # La largeur de notre ordinateur
   h = 600 # La hauteur de notre ordinateur
end
```

Et maintenant, faisons un petit ordinateur : `laptop : Ordinateur.new`. On a créé un ordinateur. Mais vous savez quoi ? 

[[erreur]]
| Ce que nous avons fait n'est pas valable.

En effet, ici nous définissons des variables, mais ce sont des variables normales pour Ruby. Si nous créons deux ordinateurs, on ne pourra pas leur donner deux largeurs différentes car les variables que nous avons créé de variables dîtes **d'instance**. Une variable d'instance est une variable qui caractérise une instance d'une classe. Ainsi, deux instances d'une même classe peuvent avoir la même variable d'instance différente. La valeur de la variable d'instance est propre à l'instance créé. Ainsi, deux ordinateurs pourront avoir la même hauteur et la même largeur.

[[information]]
| Pour créer une variable d'instance, il suffit de préfixer son nom par `@`.

Ainsi, on transforme notre classe en 

```ruby
class Ordinateur
   @w # La largeur de notre ordinateur
   @h # La hauteur de notre ordinateur
end
```

Pour le moment, on ne sait pas comment modifier la valeur de cette variable, mais on peut cette fois imaginer ce genre de code qui permettrait d'avoir deux ordinateurs de tailles différentes :

```ruby
laptop = Ordinateur.new
desktop = Ordinateur.new
# On met la largeur de laptop à 800 et celle de desktop à 1600
# On met la hauteur de laptop à 600 et celle de desktop à 800
```

Il ne faut donc pas oublier de placer le `@` au début du nom d'une variable d'instance, sans quoi notre code sera erroné.

# Une bonne classe
