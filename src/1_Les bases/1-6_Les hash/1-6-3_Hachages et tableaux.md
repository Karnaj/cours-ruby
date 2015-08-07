Bon, maintenant que nous avons vu les hachages et certaines opérations possibles sur eux, vous vous demandez sûrement pourquoi les utiliser. Nous n'avons en effet vu qu'un seul exemple jusqu'à maintenant et nous l'avons utilisé pour toutes nos opérations. 

[[question]]
| Quelles sont les avantages et les inconvénients des hachages face aux tableaux ? Lequel choisir ?

C'est ce que nous allons voir dans cette partie. Pour cela, nous allons nous attarder sur trois points :

- la clarté
- l'ordre
- la flexibilité

# La clarté

Sur ce point, les hachages sont mieux que les tableaux. En effet, alors que les clés des tableaux, ne sont que des nombres, avec les hachages, on peut choisir tout et n'importe quoi comme clé (même des nombres donc). Les hachages permettent donc de toujours avoir des clés qui ont un sens.

# L'ordre

Sur ce point, les tableaux sont nettement mieux que les hachages. En effet, les tableaux disposent d'un ordre déjà établi de part leur définition (l'élément d'indice $0$, l'élément d'indice $1$, etc.). Au contraire, les clés des hachages ne permettent pas d'établir un ordre clair. Comment Ruby ferait il pour savoir que l'élément associé à tel clé doit venir avant l'élément associé à tel clé ?

Cette absence d'ordre dans les hachages est d'ailleurs ce qui produit l'impossibilité de certaines actions possibles sur les tableaux. En effet, nous avons vu par exemple que l'opérateur `+` ne s'utilisait pas sur les hachages. Vous êtes vous demandé quelle est la raison de cela ? En fait, avec deux tableaux, l'opérateur `+` ajoute les éléments du deuxième tableau au éléments du premier tableau **en conservant l'ordre**. Ainsi, en faisant `[2, 3] + [4, 5]`, on obtient bien `[2, 3, 4, 5]` et non `[2, 3, 5, 4]` ni `[4, 5, 2, 4]`. Cela n'est pas possible avec les hachages. De même l'opérateur `<<` qui ajoute un élément à la fin d'un tableau n'est pas disponible avec les hachages (on ne sait pas où est la fin d'un hachage).

[[question]]
| Et si on donnait comme clé à nos hachages des nombres, ça marcherait, non ?

Allons-y, testons ce code :

```ruby
hachage = {1 => 1,
           2 => 2,
           3 => 3
}

hachage.each do |cle, valeur| 
   puts "#{cle} : #{valeur}"
end
```

Les éléments sont affichés dans le bon ordre. Super !

Mais, regardons maintenant ce code :

```ruby
hachage = {1 => 1,
           2 => 2,
           3 => 3
}

hachage[5] = 5
hachage[4] = 4

hachage.each do |cle, valeur| 
   puts "#{cle} : #{valeur}"
end
``` 

La clé `5` est passé avant la clé `4`. On perd notre ordre et pourtant nous n'avons fait rien d'autre qu'un simple ajout de valeurs.

[[attention]]
| N'essayez pas de faire passer un tableau pour un hachage. Les propriétés d'ordre du tableau ne seraient pas
| du tout respectées.
 
# La flexibilité

Voyons un peu les différentes opérations possibles sur les tableaux et les hachages et comparons les :

- l'ajout d'élément est possible sur les deux 
- la modification est possible sur les deux
- la concaténation n'est possible que sur les tableaux mais correspond juste à une suite d'ajout d'élément

Les hachages et les tableaux ont l'air aussi flexible l'un que l'autre. Les opérations qu'on peut effectuer sur les deux sont complètes et permettent de modifier radicalement la structure. 

Finalement, aucune structure n'est mieux que l'autre. Elles ont toutes les deux leurs points forts et leurs points faibles. Et vous savez quoi ? C'est tout simplement parce qu'elles ne sont pas adaptées aux même situations. Les tableaux sont utiles dans certains cas, les hachages dans d'autres.