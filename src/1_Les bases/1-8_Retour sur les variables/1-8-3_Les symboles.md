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

Les symboles sont surtout utilisées en lieu et place des chaines de caractères.


# Les symboles et les hachages
