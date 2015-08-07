En Ruby, vous pouvez convertir des variables (changer le type de la variable) en utilisant une **méthode**.  
Nous verrons ce qu'est une **méthode** dans un autre chapitre. Vous pouvez pour le moment considérer qu'une méthode nous permet d'effectuer une action. Ici vous devez juste mettre à la fin de votre variable l'une de ces expressions :

Code  |  Action
------|------
.to_s  |  Convertir en chaine de caractère (`string`)
.to_i  |  Convertir en entier (`int`)
.to_f  |  Convertir en flottant (`float`)
.to_a  |  Convertir en tableau (`array`)

### Exemple

```ruby
> x = 3
=> 3
> x.to_s
=> "3"
```

[[attention]]
| Si vous essayez de convertir une chaine de caractère qui n'est pas un nombre en entier (`int`) ou en flottant (`float`), vous obtiendrez 0 pour la conversion en entier, et 0.0 pour la conversion en flottant. Regardez :

```
> x = "Hello"
=> "Hello"
> x.to_i
=> 0
> y = "zeste"
=> "zeste"
> y.to_f
=> 0.0
```

Alors que :

```
> x = "3"
=> "3"
> x.to_i
=> 3
> x.to_f
=> 3.0
```

Cette conversion peut s'avérer très utile lorsque vous avez par exemple un nombre que vous voulez concaténer à une chaine de caractères.

Notez cependant que cette conversion ne modifie pas la variable. Elle vous donne une nouvelle valeur que vous pouvez récupérer dans une variable, mais la variable initiale garde son ancienne valeur.