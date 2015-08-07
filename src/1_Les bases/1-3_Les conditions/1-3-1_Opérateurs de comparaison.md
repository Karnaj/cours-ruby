Les conditions (ainsi que les boucles) introduisent de nouveaux opérateurs.
Voici le tableau des opérateurs de comparaison.

Opérateur | Signification
-----|-----
  <  |  Strictement inférieur à
  >  |  Strictement supérieur à
  <= |  Inférieur ou égal à
  >= |  Supérieur ou égal à
  == |  Égal à
  != |  Différent de

Ainsi, on a `2 < 3` qui est vrai et `3 != 2` qui est aussi vrai.

On peut aussi combiner ces opérateurs et faire des comparaisons plus avancées avec trois mots clés :

- `and` qui signifie  « et » permet d'écrire `3 > 2 and 3 < 5` (ce qui est vrai). 
- `or` qui signifie  « ou » permet d'écrire `3 > 2 or 2 < 5` (ce qui est vrai).
- `not` qui signifie « non » c'est à dire la condition contraire, permet d'écrire `not 3 < 2` (ce qui est vrai).

Sachez que l'on peut remplacer `and` par `&&`, `or` par `||` et `not` par `!`.

Essayez de taper quelques expressions avec ces signes sur Irb. 

```
2 > 1
=> true
3 > 6.0
=> false
"Trois" = "Trois"
=> true
```

Ces expressions renvoient `true` ou `false`. Ce sont ce que l'on appelle des **booléens**. Une variable booléenne ne peut prendre comme valeur que `true` ou `false`, c'est à dire vrai ou faux. Parfait pour faire des conditions.

[[information]]
| Notez que la comparaison entre chaines de caractères se fait suivant l'ordre lexicographique. Ainsi, 
| `"Trois" > "Quatre"` renverra `true`.

Vous pouvez bien sûr créer des variables de types booléens. Par exemple :

```ruby
booléen = true
faux = false
``` 

Ces booléens nous servent justement à construire nos conditions. Toutes les comparaisons que nous ferons vaudront soit `true`, soit `false` et il nous faudra juste évaluer cette valeur.

# Parenthésage 

Vous pouvez placer des parenthèses autour de vos comparaisons. Si vous les placez autour de toute la condition, cela ne change pas sa valeur. `(1 == 2 or 2 == 2)` est strictement équivalent à `1 == 2 or 2 == 2`. Cependant, si vous placez des parenthèses seulement autour d'une partie de la conditions, sa valeur peut changer. En effet, cela change les priorités. Ainsi :

- `(1 == 1 or 2 == 3) && 3 == 4` vaut `false`.
-  `1 == 1 or (2 == 3 && 3 == 4)` vaut `true`.

Voyons ce qui se passe dans le premier cas :

`1 == 1 or 2 == 3` vaut `true`, donc c'est équivalent à `true && 3 == 4`, avec $3 \neq 4$, donc `(1 == 1 or 2 == 3) && 3 == 4` vaut `false`.

Dans le deuxième cas maintenant :

`2 == 3 && 3 == 4` vaut `false`, donc c'est équivalent à `1 == 1 or false`, avec $1 = 1$, donc `1 == 1 or (2 == 3 && 3 == 4)` vaut `true`.