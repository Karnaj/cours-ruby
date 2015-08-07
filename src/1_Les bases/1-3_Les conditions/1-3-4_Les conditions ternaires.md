Si vous venez d'autres langages, peut-être connaissez vous les conditions ternaires. Elles sont un moyen condensés d'écrire des conditions. Voici le schéma qu'elles suivent : 

```ruby
condition ? (si true) : (sinon)  
```

Ce n'est pas aussi impressionnant que ça en a l'air. Il faut bien sûr s'habituer à la syntaxe, mais une fois celle-ci assimilée, il faut s'exercer pour réussir à les maîtriser. 

```ruby
age = 19

(age < 18) ? (print "Mineur") : (print "Majeur")
``` 

Et, on peut même utiliser des conditions ternaires imbriquées pour obtenir du `else if` :

```ruby
age = 19

(age < 18) ? (print "Mineur") : (age < 80 ? (print "Majeur") : (print "Senior"))
```  

Là c'est plus compliqué, non ? Prenez le temps de bien comprendre le code. 

Ne vous inquiétez pas, les ternaires sont rares, et vous n'aurez sûrement pas à les utiliser, mais vous aurez peut-être l'occasion de les croiser dans un code. En fait, les structures que vous utiliserez le plus sont la structure `if - else` et la structure `case - when`.