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

# Les variables

# Une bonne classe
