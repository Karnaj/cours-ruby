Les tableaux vous rappellent peut-être les chaines de caractère. Après tout, la concaténation se fait de la même manière pour les tableaux que pour les chaines de caractères. De même, l'ajout d'élément se fait de la même manière, à l'aide de l'opérateur `<<`. On est alors en droit de se demander si cela va plus loin.

[[question]]
| C'est vrai ça, quel est le lien entre les tableaux et les chaines des caractères ?

Si nous vous disions qu'une chaine de caractères est un tableau de nombres, nous serions en train de mentir. Mais le fait est là, on peut presque voir une chaine de caractères comme un tableau de caractères. De là, on voit la multitude d'opérations que l'on peut effectuer sur les chaines de caractères.

# Accéder à un élément

Vous l'avez sûrement déjà deviné, on accède à un élément d'une chaine de caractère à l'aide des crochets. Ainsi, si on veut obtenir le cinquième caractère d'une chaine de caractère, on peut utiliser ce code :

```ruby
chaine = "Bonjour"
print chaine[3] # Affiche 'j'
``` 

De même que pour les tableaux, l'élément d'indice $i$ correspond à l'élément $i + 1$ de la chaine de caractère. 

De plus, vous pouvez toujours, à la manière des tableaux, afficher une partie d'une chaine de caractère à l'aide des intervalles. Pour afficher « onj » de la chaine « bonjour » :

```ruby
chaine = "Bonjour"
print chaine[1..3]
```

# Parcourir une chaine de caractère

Nous avons déjà vu dans le chapitre précédent qu'il était possible de parcourir une chaine de caractères avec une boucle `for`. On parcourait ainsi un par un les éléments, le séparateur étant le `\n`. Maintenant que nous savons accéder à un caractère grâce à son indice, on peut parcourir toutes les lettres de la chaine de caractère.

```ruby
chaine = "bonjour"
for i in [0..6]
   print "#{chaine[i]} "
end
```

Mais là encore, ce n'est pas cette méthode que nous utiliserons pour parcourir tous les caractères d'une chaine. Trouverez vous la méthode que nous utiliserons ? 

La méthode `each` ? Perdu, mais presque. Nous utiliserons la méthode `each_char` (chaque caractère). Elle s'emploie de la même manière que `each`, mais est spécifique aux chaines de caractères. Vous voyez bien là que même si les chaines de caractères et les tableaux se ressemblent, ils ne sont pas pareils. Réécrivons le code précédent : 

```ruby
chaine = "bonjour"
chaine.each_char do |c|
   print "#{c} "
end
```