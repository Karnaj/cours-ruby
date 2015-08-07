Il est maintenant temps de parler d'une boucle particulière : la boucle `loop`. Elle a de particulière qu'elle n'a pas de conditions d'arrêt, c'est une boucle infinie. Elle est donc équivalent à `while(true)`. Mais nous pouvons quand même en sortir. Comment ? Tout simplement en utilisant un des mots-clés que nous venons de voir. Oui, le mot-clé `break` permet de sortir d'une boucle infinie. Testez d'abord ce code (attention, ce programme boucle indéfiniment, il vous faudra appuyer sur ||Ctrl + C|| pour quitter le programme) :

```ruby
i = 0
loop do
   puts i
   i = i + 1
end
```   

Et regardez celui-là qui s'arrête à $10$ grâce à `break`

```ruby
i = 0
loop do
   puts i
   break if i == 10
   i = i + 1
end
```

[[attention]]
| Le `do` est obligatoire, de même que le `end`. En fait, `do` peut aussi être utilisé de la même manière 
| avec les boucles `while`, `until` et `for`. Le code de la boucle est alors encadré par `do` et `end` de 
| même qu'il est encadré par `begin` et `end` dans la structure `begin - while`. 

Tout comme nous vous avons dit que les structures conditionnelles que vous utiliserez le plus sont `if - else` et `case - when`, nous devons vous avouer que les boucles les plus courantes sont les boucles `while` et `for`. Et encore, vous n'utiliserez presque jamais `for` de cette manière. La boucle `for` sera utilisée avec ce que l'on appelle des itérateurs. La boucle `loop` que nous venons de voir est elle préférée à la structure `begin - while`.