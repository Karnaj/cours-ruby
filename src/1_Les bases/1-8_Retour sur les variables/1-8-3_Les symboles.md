# Garder le même identifiant

Il peut arriver que l'on veuille attribuer un objet unique à une variable, c'est à dire garder le même identifiant. C'est le but des symboles. On peut alors voir les symboles comme un nom associé à un identifiant. Donc chaque fois qu'une variable aura pour valeur ce symbole, ce sera toujours le même identifiant qui lui sera associé. Un symbole en Ruby c'est **un nom précédé du caractère `:`. Donc :

```ruby
symbole = :symbole
```

C'est un symbole. Vérifions alors que deux symboles identiques ont le même identifiant :

```ruby
x = :symbole
y = :symbole
print x.object_id == y.object_id
```

Ce code affiche `True`. Toutes les variables qui auront pour valeur `:symbole` sont le même objet. Que ce soit dans une fonction ou autre part :

```ruby
def f
   y = :s
   puts y.object_id
end

def g
   z = :s
   puts z.object_id
end

x = :s
puts x.object_id
puts :s.object_id
f
g
```

Nous obtenons bien le même identifiant partout.

[[question]]
| Mais quel est l'intérêt de cette démarche ? 

Imaginez par exemple que vous deviez utiliser un très grand nombre de variables avec le même contenu. En utilisant les symboles, nous faisons une économie de mémoire (un seul objet plutôt que plusieurs). 

# Les symboles et les chaines de caractères

Les symboles sont surtout utilisées en lieu et place des chaines de caractères. La question qui se pose alors est quand utiliser les symboles et quand au contraire utiliser des chaines de caractères. La réponse est en rapport avec l'information qui est importante :

- si c'est le contenu qui est important, utilisez une chaine de caractères ;
- si c'est l'identité qui importe, utilisez un identifiant.

Prenons l'exemple d'une application qui gère les nationnalités de plusieurs individus. Ce qui nous intéresse, c'est l'information de la nationalité et non pas comment cette nationalité s'écrit. En fait, on pourrait tout aussi bien écrire `français` que `France` ou encore `fr`. Par contre, le nom de l'individu sera une chaine de caractère. On va donc plutôt écrire :

```ruby
nom_1 = "Nom"
nation_1 = :fr
nom_2 = "Nom2"
nation_2 = :en
nom_3 = "Nom3"
nation_3 = :it # it c'est Italie pas informatique, on est bien d'accord
```

Pour convertir un symbole en chaine de caractère, On peut toujours utiliser la méthode `to_s`. Cependant, vous pouvez également utiliser la méthode `id2name`. 

L'opération inverse (à savoir convertir une chaine de caractères en symboles) est faite à l'aide de la méthode `intern`. Donc :

```ruby
nom = "nom"
nation = :fr
x = nom.intern # x = :nom
y = nation.to_s # y = "fr"
z = nation.id2name # z = "fr"
```

# Les symboles et les hachages

Les symboles sont communément utilisés en tant que clés pour les hachages. 
