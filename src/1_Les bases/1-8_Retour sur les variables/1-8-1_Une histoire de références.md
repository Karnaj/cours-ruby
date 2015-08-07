# Qu'est-ce qu'une variable ?

Vous êtes vous déjà posé cette question ? Nous les utilisons depuis le premier chapitre de ce tutoriel et vous ne vous êtes jamais posé la question ? Bon, cela doit changer, voyons un peu ce qui se passe quand on déclare une variable. 

Si vous venez d'autres langages peut-être vous a t-on dit qu'une variable était une boîte. Une simple boîte dans laquelle on range une valeur. Pour accéder à cette valeur, on ouvre la boîte. Pour changer la valeur d'une variable, on change le contenu de cette boîte. Simple, non ?

Si c'est cette idée que vous avez en tête, il vous faudra la supprimer. En Ruby, une variable n'est rien d'autre qu'un nom.

[[question]]
| Quoi, un nom ? Dans ce cas, pourquoi ce nom représente une valeur ?

Le verbe utilisé dans la question est intéressant. Le nom **représente** une valeur. C'est exactement ça. Une variable n'est pas une boîte qui contient quelque chose, c'est juste un nom qui représente une valeur. 

[[attention]]
| Bien sûr, pour cela, la variable doit contenir quelque chose pour savoir ce qu'elle est censée représenter.

Une représentation plus juste des variables pourraient être les pointeurs dans les langages comme le C (à un plus haut-niveau). Un pointeur est une variable qui contient une adresse mémoire. Si deux pointeurs sont égaux, alors non seulement la valeur pointée est la même, mais en plus l'adresse mémoire est la même. 

En Ruby, cela se vérifie ainsi, si `a = 4` et `b = 4`, alors non seulement les valeurs `a` et `b` sont égaux, mais en plus, ils représentent le même objet en mémoire (on ne peut pas vérifier leur adresse mémoire, mais on peut vérifier leur identifiant). Il n'y a pas un objet créé pour `a` et un autre pour `b`, leur identifiant est le même. Ce sont des **références** au même objet. 

# Une histoire d'identifiant

Mettons maintenant un nom sur ce dont nous parlons. Nous avons dit qu'une variable servait juste à représenter une valeur. Puis nous avons parlé d'identifiant. Le mot « identifiant » est le bon. D'ailleurs, il existe une méthode qu'on peut utiliser avec tout en Ruby, la méthode `object_id`. Cette méthode donne l'identifiant d'une variable. 

Utilisons cette méthode pour vérifier ce que l'on a dit dans la partie précédente.

```ruby
a = 4
b = 4
puts a.object_id
puts b.object_id
``` 

Comme nous l'avons dit, les deux variables ont le même identifiant. 

Nous pouvons même aller encore plus loin :

```ruby
a = 4
b = 4
puts a.object_id
puts b.object_id
puts 4.object_id
```

Bien sûr en affectant `a` à `b`, ils ont également le même identifiant :

```ruby
a = 4
b = a
puts a.object_id
puts b.object_id
```

## Tableaux, chaines de caractères...

Cependant, l'affaire est différente pour les tableaux, chaines de caractères ou encore hachages. Lorsque vous créez deux fois le même tableaux par exemple, ils n'ont pas le même identifiant. Regardez ce code :

```ruby
a = [122, 32]
b = [122, 32]
puts a.object_id
puts b.object_id
puts [122, 32].object_id
```

Comme vous pouvez le remarquer en exécutant ce code, les trois identifiants sont différents. Vous ne voyez pas la raison de cette différence mais ne vous inquiétez pas, c'est dû à comment nous pouvons modifier ces variables (et donc ce sera traité dans la partie qui suit).
 
# Modification de variables

Dans cette partie, nous allons tenter de répondre à une question simple.

[[question]]
| Que se passe t-il lorsque l'on modifie une variable ?

La question est simple, mais vous allez voir que la réponse ne l'est pas forcément.

Commençons par le cas de variables simples. Regardez le résultat de ce code :

```ruby
a = 12
puts a.object_id
a = 15
puts a.object_id
```

Ce code conforte notre idée précédente : `a` ne fait plus référence au même objet, son identifient n'est donc plus le même. 

Maintenant que nous avons vu ce qui se passe lors de la modification de variable, nous pouvons passer à la partie suivante. Ah, non, il nous reste le cas des tableaux, des chaines de caractères et des hachages qui comme tout à l'heure sont particuliers. 

```ruby
a = []
puts a.object_id
a = [1, 2]
puts a.object_id 
```

Les identifiants sont différents comme tout à l'heure.

[[question]]
| Quoi ? Pourquoi ? Pourtant, nous avons dit que ce cas était différent ?

Oui, mais attendez un peu. Le fait est qu'ici on change de tableau. Au départ, `a` faisait référence au tableau `[]`, après la seconde affectation, il fait référence au tableau `[1, 2]`. 

Cependant, lorsque nous modifions le tableau directement (donc sans affectation), la variable fait toujours référence au même tableau. Aucun nouveau tableau n'a été créé, c'est l'ancien tableau qui a été modifié.

```ruby
a = []
puts a.object_id
a << 1
a << 2
a[0] = 23
puts a.object_id 
```

Dans ce code, nous ne réaffectons pas notre variable `a`. Elle fait toujours référence au même tableau, tableau qui en revanche a été beaucoup modifié. L'identifiant reste néanmoins le même.

Et ceci nous permet de répondre à la question que nous nous posions à propos de la différence entre les tableaux et les variables plus simples : si en déclarant deux fois le même tableau les deux variables avaient le même identifiant, alors en modifiant l'un on modifierait l'autre ce qui n'est pas trop voulu. Voilà ce qu'on veut (et c'est ce qui se passe) :

```ruby
a = []
b = [] # l'id de b est différent de celui de a
a << 1 # a est modifié, cela ne change pas b
c = a # c = a donc c et a ont le même identifiant
c << 2 # On modifie c, a est également modifié car ils font référence au même tableau
a = [] # on donne une nouvelle valeur à a, c garde son ancienne valeur par contre
```

Cette partie était remplie de nouvelles informations. Prenez le temps de bien tout assimiler avant de passer à la suite. Faites vos propres tests et une fois que vous serez prêts, continuez.