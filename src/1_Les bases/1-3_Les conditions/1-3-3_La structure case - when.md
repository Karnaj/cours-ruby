La structure `case - when` est une autre structure de condition. Elle permet de tester une suite de conditions sur une variable. Si la variable vaut telle valeur, alors fait ceci, sinon si elle vaut telle autre valeur, alors fait ça... Par exemple, écrivons un programme qui demande à l'utilisateur d'entrer « Un », « Deux » ou « Trois » et qui affiche la valeur numérique du nombre entré :

```ruby
nombre = gets.chomp

case nombre # On teste la valeur de nombre
   when "Un" # Si c'est "Un"
      print 1
   when "Deux" # Sinon si c'est "Deux"
      print 2
   when "Trois" # Sinon si c'est "Trois"
      print 3
end   
```

Vous remarquez que là encore il y a un `end`. Il est aussi **obligatoire**. 

Notez que nous pouvons rajouter un `else` pour faire quelque chose si aucun des cas testés n'est vérifié :

```ruby
nombre = gets.chomp

case nombre 
   when "Un"
      print 1
   when "Deux"
      print 2
   when "Trois"
      print 3
   else
      print "La saisie n'est pas bonne." 
end
```
 
Si la saisie de l'utilisateur n'est ni « Un », ni « Deux », ni « Trois », alors on affiche « La saisie n'est pas bonne ».

# Les intervalles

Cependant, là où `case` s'avère vraiment utile, c'est qu'il permet de tester si une valeur est dans un intervalle. 

En Ruby, nous allons noter un intervalle `x..y`, qui représente l'intervalle $[x, y]$ (donc $x$ et $y$ sont inclus). Pour voir comment nous pouvons utiliser cela, prenons l'exemple d'un programme qui vérifierait  l'admission ou la mention selon une note à un examen. Dans notre cas, avoir en dessous de 6 est un échec, au-dessus de 12 la mention assez bien, de 14 la mention bien et de 16 la mention très bien.  

Faire ce programme avec des `if` et des `else` serait long et contraignant. La structure`case` permet de simplifier les choses en offrant plusieurs choix. Voyez plutôt :

```ruby
note = 18 #Modifiez la note ici et voyez le résultat

case note
   when 0..6
      print "Vous n'avez pas réussi l'examen"
   when 6..12
      print "Vous avez réussi l'examen"
   when 12..14
      print "Vous avez réussi l'examen avec mention assez bien"
   when 14..16
      print "Vous avez réussi l'examen avec mention bien"
   when 16..20
      print "Vous avez réussi l'examen avec mention très bien"
   else
      print "La note entrée est incorrecte"
end
```

N'essayez même pas imaginer la ~~galère~~ l'embêtement que ça aurait été avec des `if` et des `else`.

[[information]]
| Les intervalles peuvent aussi se faire avec des valeurs flottantes. Ainsi, nous pouvons choisir 
| d'attribuer la mention `when 16.5..20`.