Nous allons maintenant nous intéresser à une classe vous connaissez déjà sans le savoir : *Fixnum*. Cette classe sert à représenter les entiers pouvant être stockés dans un unique mot de la mémoire (ou en français : les petits entiers, jusqu'à 536 807 912 quand même :) ). Ainsi, tout nombre supérieur à 536 807 912 sera de type *Bignum*. Vous avez donc manipulé beaucoup de *Fixnum* jusqu'à présent sans même savoir que vous utilisiez un objet ! Faisons les présentation en créant un *Fixnum* :

```ruby
fix = 5
```

Comme dit plus tôt, les objets ont des méthodes qui ne demandent qu'à être utilisées. Essayons d'obtenir la valeur absolue de notre entier avec sa méthode `abs`. Pour cela, il nous faut écrire le nom de la variable puis celui de la méthode avec un point entre deux.

```ruby
fix.abs # la méthode/fonction ne prenant pas de paramètre, les parenthèses sont facultatives
```

Comme vous vous en doutez, nous avons obtenu un nouvel objet... de type *Fixnum* ! Essayons une autre méthode : `succ` qui permet d'avoir le successeur notre entier (entier + 1).

```ruby
temporaire = fix.abs
temporaire.succ

# ou
fix.abs.succ
# peut être écrit (fix.abs).succ
# montrant ainsi que c'est la méthode succ du résultat de fix.abs qui est appelée
```

Enfin, nous allons vous apprendre une terrible vérité : les opérateurs mathématiques que vous utilisiez jusqu'à présent **sont des méthodes**. Voici un petit exemple :

```ruby
a = 5
b = 6

a.+(b)
a + b # même résultat

a.succ.+(b).succ # ça fait combien ? :p
```