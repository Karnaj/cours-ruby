# Les modules

Un module est un genre de structure regroupant à la fois des variables et des méthodes. Cependant, **un module n'est pas une variable**. En effet, un tableau contient lui aussi des variables et des méthodes, mais ce n'est pas pour autant un module.

Un module permet de partager du code avec d'autre structure du langage, comme d'autres modules, ou encore des *classes* (mais nous aborderons ces choses la dans la prochaine partie). Cela permet de réduire le nombre de ligne de code à écrire, et de coller au principe *DRY*. En effet, il n'est pas utile de réécrire deux fois la même fonction ! On peut alors réunir dans un module des variables et des méthodes qui ont un lien et ensuite utiliser ce module dans plusieurs programmes. On peut par exemple imaginer un module mathématique contenant des fonctions trigonométriques et divers outils mathématiques.

Pour info, un module se construit de cette façon.

``` ruby
module Multiplication
  CONSTANTE = 2
  
  def Multiplication.table x
    print "On a demandé la table de 2"
  end
end
```

Un module commence par le mot-clé `module` et se finit par le mot-clé `end`. Après le mot-clé `module`, on écrit le nom du module (ici `Multiplication`). Ce nom doit commencer par une majuscule sinon nous obtiendrons l’erreur « class/module name must be CONSTANT ». Ensuite, on va à la ligne et on écrit comme dans un fichier normal.

Ici, nous avons défini la constante `CONSTANTE` et la fonction `table`. Les constantes des modules sont nommés comme d’habitude, c’est-à-dire avec le première lettre en majuscule. Cependant, pour définir la fonction `table`, nous avons écrit `Multiplication.table` et pas `table`. Cela s’explique par le fait qu’il faut que Ruby sache que nous sommes en train de définir une fonction du module `Multiplication`. `Multiplication.table` peut alors se lire « la fonction `table` du module `Multiplication` ». Finalement, pour écrire une fonction dans un module, nous écrirons `def nom_du_module.nom_de_la_fonction`.

[[information]]
| Nous avons un niveau d’indentation dans notre module. C’est une bonne pratique qui facilite la relecture.

# Utiliser un module 


# Mettre un module dans un fichier séparé

*[DRY]: Don’t Repeat Yourself
