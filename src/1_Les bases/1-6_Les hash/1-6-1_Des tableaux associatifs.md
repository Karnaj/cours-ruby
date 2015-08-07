# Qu'est-ce qu'un hachage

Nous avons dit que nous allions voir un nouveau type de conteneur. En fait, un hachage n'est rien d'autre qu'un tableau spécial. Le nom tableau associatif peut vous aider à comprendre en quoi ils sont spéciaux. En fait, au lieu d'associer une valeur à un nombre entier comme dans un tableau normal, nous allons associer une valeur à... ce que nous voulons. Nous pourrons par exemple associer à une chaine de caractères une autre chaine de caractères. 

```ruby
tableau[2] # Un tableau normal
hachage["deux"] # Ce qu'on peut faire avec un hachage
```

L'idée générale est simple à comprendre.

[[question]]
| Mais, à quoi ça sert ?

Bonne question. Supposons que notre but est de stocker des informations sur une personne. Nous voulons son nom, son prénom et son âge. Nous pourrions créer un tableau normal :

```ruby
   personne = ["nom de la personne", "prenom de la personne", "age de la personne"]
```

Mais ce ne serait pas très évident à utiliser. Un tableau associatif serait bien mieux. On aurait un tableau associatif à trois cases :

- la case `"nom"` associé à son nom
- la case `"prenom"` associé à son prénom
- la case `"age"` associé à son âge

Ce sera non seulement plus facile à écrire, mais aussi à lire (n'oubliez pas que si on passe beaucoup de temps à écrire un programme, on passe encore plus de temps à le lire).

[[information]]
| On appelle clé (« key » en anglais) ce qu'on a choisi comme identifiant, et on appelle valeur ce à quoi
| on accède grâce à la clé (les éléments du hachage).

Dans notre exemple, `nom`, `prenom` et `age` seraient donc des clés alors que le nom de la personne, son prénom et son âge seraient des valeurs.

# Déclarer un hachage

Maintenant que nous savons ce que sont les hachages et que nous savons à quoi ils peuvent servir, il ne nous reste plus qu'à les utiliser. Pour déclarer un hachage, il faut utiliser des accolades à la place des crochets du tableau. Pour déclarer un hachage vide, il faut donc utiliser 

```ruby
hachage = {}
```

On peut l'afficher avec `print` :

```ruby
hachage = {}
print hachage
```

Code qui nous affiche bien entendu ${}$.


De plus, pour indiquer qu'on associe une valeur à une autre, il faut utiliser `=>`. Les éléments sont, comme pour les tableaux, séparés par une virgule. Déclarons le hachage de notre exemple précédent :

```ruby
hachage = {"nom"    => "Mon nom",
           "prenom" => "Mon prenom",
           "age"    => 2015
}
print hachage
``` 

Cette fois, on obtient affiché à l'écran : « {"nom"=>"Mon nom", "prenom"=>"Mon prenom", "age"=>2015} ».

[[attention]]
| Contrairement aux tableaux, les hachages ne peuvent pas être déclarés sans utiliser les accolades, elles 
| sont obligatoires.

Nous avons dit que nous pouvions utiliser n'importe quoi comme clé. Faisons un hachage avec des nombres et des chaines de caractères comme clé :

```ruby
hachage = {"abc" => "dcvs",
           2     => "deux",
           3.4   => 23
}  
print hachage
```

Et on obtient : « {"abc"=>"dcvs", 2=>"deux", 3.4=>23} ».