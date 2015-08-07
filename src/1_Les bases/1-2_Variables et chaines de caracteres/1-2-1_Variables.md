Sans vous en rendre compte, vous avez déclaré deux variables dans le chapitre précédent : `x` et `y`.  

[[question]]
| Mais, c'est quoi une variable ?

Une variable est une donnée de votre programme, stockée dans votre ordinateur. En fait, dans notre programme, ce sera juste un nom (on parle d'**identifiant**) auquel on associe une valeur, un mot... On peut donc avoir une variable qui s'appelle `age` et qui contient l'age de l'utilisateur. Dans le chapitre précédent, nous avons utilisé `x` et `y` pour stocker des nombres afin de faire des calculs. 

# Déclaration de variables et opérations

Comme vous avez pu le voir, la déclaration d'une variable est enfantine : un simple signe égal.  
Vous pouvez ensuite effectuer les mêmes opérations avec vos variables qu'avec des nombres : additions, soustractions, multiplications et divisions.

```ruby
> x = 3
=> 3
> y = 2
=> 2
> x + y
=> 5
> x - y
=> 1
```

On peut changer la valeur d'une variable au cours d'un programme. On dit qu'on lui **assigne** une valeur. Une variable a pour valeur la dernière valeur qui lui a été assignée. Par exemple, regardons ce code :

```ruby
> x = 3
=> 3
x = 5
=> 5
```

Après cela, la variable `x` ne vaudra plus $3$ mais vaudra bien $5$.

Vous pouvez récupérer le résultat d'une opération entre variables dans une nouvelle variable (ou même dans l'une des variables avec laquelle vous faites l'opération) :

```ruby
> a = 3
=> 3
> b = 2
=> 2
> c = a + b
=> 5
```

`c` vaut $5$.

```ruby
> a = 3
=> 3
> b = 2
=> 2
> a = a + b
=> 5
```

`a` vaut $5$.

# La valeur `nil`

Avez vous déjà essayé d'utiliser une variable sans lui donner une valeur en la déclarant ? Voici ce que l'on obtient (pour déclarer la valeur sans l'initialiser, il suffit d'écrire `variable = `) :

```ruby
> variable =
> variable
=> nil
```

[[question]]
|Que signifie cette valeur `nil`

`nil` est une valeur particulière qui signifie l'absence de valeur justement. Notre valeur n'a ici aucune valeur. 

Pour le moment, savoir cela ne vous sera pas très utile, mais gardez cette idée en mémoire : `nil` représente l'absence de valeur.

# Constantes

Une constante est une variable dont vous ne pouvez pas modifier la valeur. Elle reste la même pendant tout le programme.   

Pour déclarer une constante, rien de plus simple ...

```ruby
> PI = 3.14159265359
=> 3.14159265359
```

... Il suffit de commencer le nom d'une variable par une majuscule. C'est imposé par le langage. Ainsi, vous ne pouvez pas commencer le nom d'une variable normale par une majuscule, vous aurez alors déclaré une constante. En essayant de modifier la valeur d'une constante vous aurez un avertissement (mais la valeur sera quand même changée). Ainsi si j'essaye de modifier la constante `V`, j'obtiens :

```
warning: already initialized constant V
warning: previous definition of V was here
```

Notez que nous écrivons le nom de la constante tout en majuscules, entre autres parce que c'est la convention de nombreux langages, mais aussi pour pouvoir les repérer plus facilement.

# Conventions de nommage

Nous avons commencé à parler de conventions de nommages pour les constantes. Continuons à en parler. Tout d'abord, nous devons préciser que tous les noms de variables ne sont pas possibles. Il y a des règles :

- un nom de variable ne peut pas commencer par un chiffre
- un nom de variable ne peut pas contenir de caractères accentués
- un nom de variable ne peut pas contenir de signes de ponctuation
- un nom de variables ne peut pas contenir de symboles opératoires (`+`, `-`, `*`, `/`, `%`) 

À cela, il faut ajouter qu'un certains nombre de mots ne peuvent pas être utilisés comme noms de variables. Ce sont des mots réservés pas Ruby. Ils font partie du langage et ont un sens propre qui fait qu'on ne peut pas les utiliser. Les voici :

+--------------+--------------+--------------+--------------+--------------+--------------+
|   `=begin`   |    `break`   |    `elsif`   |   `module`   |    `retry`   |   `unless`   |
+--------------+--------------+--------------+--------------+--------------+--------------+
|    `=end`    |    `case`    |     `end`    |    `next`    |   `return`   |   `until`    |
+--------------+--------------+--------------+--------------+--------------+--------------+
|    `BEGIN`   |    `class`   |   `ensure`   |     `nil`    |    `self`    |    `when`    |
+--------------+--------------+--------------+--------------+--------------+--------------+
|     `END`    |     `def`    |    `false`   |     `not`    |    `super`   |   `while`    |
+--------------+--------------+--------------+--------------+--------------+--------------+
|    `alias`   |  `defined?`  |     `for`    |     `or`     |    `then`    |   `yield`    |
+--------------+--------------+--------------+--------------+--------------+--------------+
|     `and`    |     `do`     |     `if`     |    `redo`    |    `true`    |`\_\_FILE\_\_`|
+--------------+--------------+--------------+--------------+--------------+--------------+ 
|    `begin`   |    `else`    |     `in`     |   `rescue`   |    `undef`   |`\_\_LINE\_\_`|
+--------------+--------------+--------------+--------------+--------------+--------------+ 

De plus, il est conseillé d'écrire ses variables en [snake_case](https://fr.wikipedia.org/wiki/Snake_case). Cela signifie que toutes vos variables seront écrites en minuscules et que les changements de mots seront signalés par un tiret bas. 

Les constantes, elles, doivent être écrites en [SCREAMING_SNAKE_CASE](https://fr.wikipedia.org/wiki/Snake_case). Elles doivent donc écrites en majuscule, les changements de mots signalés par un tiret bas. 

```ruby
ma_super_variable
MA_SUPER_CONSTANTE  
``` 

Finalement, et là il ne s'agit que de logique simple, donnez à vos variables des noms clairs et explicites. Préférez `nom` à `n` par exemple. Et si vous codez en français, laissez vos noms de variables en français. Ne mélangez pas les noms en anglais et en français.