[[information]]
| À partir de maintenant, nos programmes seront plus conséquents et le nombre de ligne sera donc plus important. Pour écrire votre code dans des fichiers, consultez le chapitre [Ecrire le code dans des fichiers](http://zestedesavoir.com/tutoriels/373/une-introduction-a-ruby/645/annexe/3058/ecrire-le-code-dans-des-fichiers-notepad/) de la partie [Annexe](http://zestedesavoir.com/tutoriels/373/une-introduction-a-ruby/645/annexe/).

Dès à présent dans nos exemples, nous utiliseront des commentaires. Les commentaires sont des messages qui sont ignorés par l'interpréteur et qui permettent de donner des indications sur le code (car, vous vous en rendrez compte, relire ses programmes après plusieurs semaines d'abandon, sans commentaires, peut parfois être plus qu'ardu).

En Ruby, un commentaire débute par un dièse (« # ») et se termine par un saut de ligne. Tout ce qui est compris entre ce # et ce saut de ligne est ignoré. Un commentaire peut donc occuper la totalité d'une ligne (on place le # en début de ligne) ou une partie seulement, après une instruction (on place le # après la ligne de code pour la commenter plus spécifiquement).

Vous pouvez également faire des commentaires multi-lignes. Pour cela, il faut placer votre commentaire entre `=begin` et `= end`.

# Afficher des informations

Depuis le début, nous utilisons irb pour programmer en Ruby. Cependant, maintenant, lorsque nous n'utiliserons pas irb et mettrons nos programmes dans des fichiers, il nous faudra un moyen d'afficher les résultats obtenus et le contenu de nos variables. Pour cela, nous allons encore une fois utiliser une **méthode**.

Nous avons deux méthodes pour afficher des informations, `puts` et `print`. Elles ont un fonctionnement similaire à la différence près que contrairement à `print`, `puts` va à la ligne après avoir effectué l'affichage. Leur utilisation est par contre parfaitement similaire. Nous allons donc voir l'exemple de `puts`.

Pour afficher une chaine de caractère ou un nombre voici le code à utiliser :

```ruby
puts "Chaine"
puts 2
puts 3.5
```  

Ces lignes de codes vont afficher `Chaine`, aller à la ligne, afficher $2$, aller à la ligne et finalement afficher $3.5$ et... aller à la ligne.

Nous pouvons également afficher le contenu d'une variable de la même manière :

```ruby
a = 3
puts a
```

Ce programme nous affichera $3$ et un saut de ligne. 

Notez finalement qu'en utilisant la virgule pour séparer des éléments, la méthode est appelée plusieurs fois et affiche chacun des éléments. Le code `print "Bonjour", 2, 45.8` équivaut à ce code :

```ruby
print "Bonjour"
print 2
print 45.8 
``` 

Ceci vous sera très utile. Cependant, lorsque vous voulez afficher une chaîne de caractères et des variables, il vaut mieux utiliser l'interpolation de chaînes de caractères. Ainsi vous écrirez 

```ruby
print "Bonjour #{variable1} #{variable2}"   
```

plutôt que

```ruby
print "Bonjour"
print variable1
print variable2
```

Les méthodes `puts` et `print`, comme vous le voyez ne sont pas très compliquées. Nous allons maintenant voir comment demander des informations à l'utilisateur.

# La méthode gets

Si vous voulez demander des informations à l'utilisateur, la méthode `gets` est toute désignée.  
Voici comment l'utiliser :

```ruby
print "Entrez votre nom : "
prenom = gets.chomp
print "Bonjour #{prenom}"
```

Le mieux est de le voir en action et d'essayer vous-même :

```ruby
Entrez votre prénom : Zesteur
Bonjour Zesteur 
```

Après `prenom = gets.chomp`, le programme se stoppe et attend votre saisie. Il suffit de rentrer l'information à la ligne suivante et de valider en appuyant sur ||Entrée||.

[[question]]
| Pourquoi rajouter `.chomp` après le `gets` ?

En fait, c'est la méthode `gets` qui permet de demander une saisie à l'utilisateur. Elle nous renvoie une chaine de caractères. Essayons donc `prenom = gets`. Affichez maintenant `prenom`. Vous avez vu le souci ? `gets` nous laisse un `\n`. Nous ne voulons pas nous embarrasser d'un caractère gênant. Autant le supprimer tout de suite. `chomp` agit sur une chaine de caractères (ici la chaine renvoyée par `gets`) et supprime ce `\n`. Ainsi, nous aurions également pu faire :

```ruby
   prenom = gets
   prenom = prenom.chomp
```

Ici, on récupère d'abord la saisie de l'utilisateur et seulement à la ligne d'après on supprime le `\n`.

[[attention]]
| `gets.chomp` renvoie une chaine de caractères. Si on veut par exemple faire des calculs, il faudra faire 
| une conversion.

# Les caractères spéciaux

Ce `\n`, que nous venons de croiser, vous vous demandez sûrement ce que c'est ? En fait, `\n` est un caractère spécial qui représente un retour à la ligne. On parle de **caractères d'échappements** (ils sont échappés par le caractère `\`. Vous pouvez même l'utiliser pour aller à la ligne dans vos affichages. Par exemple :

```ruby
print "zeste\n" # Affiche  « zeste » et va à la ligne
print "zeste\n savoir" # Affiche « zeste », va à la ligne et affiche « savoir »  
``` 

Les caractères d'échappement peuvent être très utiles. Voyons quelques autres caractères d'échappement.

+------+--------------------------------------+---------------------+
|  Nom |             Description              |  Code de test       | 
+======+======================================+=====================+
| `\a` |  Fait un bip                         | `print "\a"`        |
+------+--------------------------------------+---------------------+
| `\b` |  Efface le caractère précédent       | `print "x\b"`       |
+------+--------------------------------------+---------------------+
| `\n` |  Va à la ligne                       | `print "x\nz"`      |
+------+--------------------------------------+---------------------+
| `\r` |  Retourne en début de ligne          | `print "xxx \rzzz"` |
+------+--------------------------------------+---------------------+
| `\s` |  Affiche un espace                   | `print "x \s z"`    |
+------+--------------------------------------+---------------------+
| `\t` |  Affiche une tabulation horizontale  | `print "x \t z"`    |
+------+--------------------------------------+---------------------+

[[attention]]
| Puisque `\` permet d'échapper des caractères pour obtenir des caractères spéciaux, si vous voulez afficher 
| un antislash, il vous faudra utiliser `\\`.

Notez que les caractères spéciaux ne sont compris qu'avec les guillemets doubles (on dit qu'ils sont échappés). `print 'Bonjour\nzz'` affichera `Bonjour\nzz`. Le seul caractère qui est échappé avec les guillemets simples est `\'` qui permet d'afficher des guillemets simples. De même, `\"` permet d'afficher des guillemets doubles lorsqu'on les utilise pour délimiter la chaine de caractère.