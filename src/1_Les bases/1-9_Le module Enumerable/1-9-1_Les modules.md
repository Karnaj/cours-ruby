# Les modules

Un module est un genre de structure regroupant à la fois des variables et des méthodes. Cependant, **un module n'est pas une variable**. En effet, un tableau contient lui aussi des variables et des méthodes, mais ce n'est pas pour autant un module.

Un module permet de partager du code avec d'autres structures du langage, comme d'autres modules, ou encore des *classes* (mais nous aborderons ces choses la dans la prochaine partie). Cela permet de réduire le nombre de ligne de code à écrire, et de coller au principe *DRY*. En effet, il n'est pas utile de réécrire deux fois la même fonction ! On peut alors réunir dans un module des variables et des méthodes qui ont un lien et ensuite utiliser ce module dans plusieurs programmes. On peut par exemple imaginer un module mathématique contenant des fonctions trigonométriques et divers outils mathématiques.

Un module se construit de cette façon.

``` ruby
module Multiplication
  MAX = 10
  
  def Multiplication.table x
    puts "On a demandé la table de #{ x }."
  end
end
```

Un module commence par le mot-clé `module` et se finit par le mot-clé `end`. Après le mot-clé `module`, on écrit le nom du module (ici `Multiplication`). Ce nom doit commencer par une majuscule sinon nous obtiendrons l’erreur « class/module name must be CONSTANT ». Ensuite, on va à la ligne et on écrit comme dans un fichier normal.

Ici, nous avons défini la constante `CONSTANTE` et la fonction `table`. Les constantes des modules sont nommés comme d’habitude, c’est-à-dire avec le première lettre en majuscule. Cependant, pour définir la fonction `table`, nous avons écrit `Multiplication.table` et pas `table`. Cela s’explique par le fait qu’il faut que Ruby sache que nous sommes en train de définir une fonction du module `Multiplication`. `Multiplication.table` peut alors se lire « la fonction `table` du module `Multiplication` ». Finalement, pour écrire une fonction dans un module, nous écrirons `def nom_du_module.nom_de_la_fonction`.

[[information]]
| Nous avons un niveau d’indentation dans notre module. C’est une bonne pratique qui facilite la relecture.

Le nom du module peut être remplacé par le mot-clé `self`, qui signifie « soi », dans la définition de ses fonctions. Ainsi, nous pouvons écrire ceci.

```ruby
def self.table x
  puts "On a demandé la table de #{ x }."
end
```

Dans une fonction d’un module, nous pouvons faire appel à d’autres fonctions du module et aux constantes du module. Pour utiliser la constante, il suffit d’écrire son nom et pour faire appel à une fonction, on écrit ``self.nom_fonction`.

```ruby
module Multiplication
  MAX = 10
  
  def self.table x
    puts "On a demandé la table de #{ x }."
  end
  
  def self.présente 
    puts "La constante MAX de ce module vaut #{ MAX }."
    puts "Essayons Multiplication.table 3."
    self.table 3
  end
end
```

Utiliser le mot-clé `self` plutôt que le nom du module est une bonne habitude. Elle permet par exemple de pouvoir changer le nom du module sans se faire de souci.

# Utiliser un module 

Utiliser un module n’est pas très compliqué. Pour utiliser une fonction d’un module, on écrit `nom_module.nom_fonction`. Par exemple, pour utiliser la fonction `table` du module `Multiplication` défini précédemment, nous allons utiliser ce code.

```ruby
print Mutltiplication.table 2
```

Bien sûr, le module doit avoir déjà été défini précédemment.

[[attention]]
| Nous ne pouvons pas utiliser le mot-clé `self` ici car Ruby ne saurait alors pas à quel module il se rapporte. Le nom du module est donc obligatoire.

Nous pouvons aussi accéder aux constantes du module. Pour cela, nous devons utiliser la syntaxe `nom_module.NOM_CONSTANTE`. Ainsi, pour accéder à la constante définie dans notre code précédent, nous allons utiliser ce code.

```ruby
print Multiplication::MAX
```

Notons que cette syntaxe fonctionne également pour utiliser les fonctions du module. Nous pouvons donc écrire `nom_module::nom_fonction`. (en revanche, nous ne pouvons pas écrire `nom_module.NOM_CONSTANTE` sous peine d’obtenir une erreur). Cependant, pour bien identifier les appels aux fonctions et les utilisations des constantes, nous allons privilégier l’écriture `nom_module.nom_fonction`. 

```ruby
module Multiplication
  MAX = 10
  
  module_function
  def self.table x
    puts "On a demandé la table de #{ x }." if x <= M
  end
end

puts "le maximum est #{ Multiplication::MAX }"
Multiplication.table 3                          # Bonne écriture.
Multiplication::table 3                         # Écriture déconseillée.
```

# Mettre un module dans un fichier séparé

*[DRY]: Don’t Repeat Yourself
