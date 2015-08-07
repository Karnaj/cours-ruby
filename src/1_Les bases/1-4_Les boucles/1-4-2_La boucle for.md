Pour le moment, nous avons vu la boucle `while` et ses dérivés. Elle permet d'exécuter des instructions en fonction d'un condition. La boucle `for` est relativement : elle permet d'exécuter des instructions pour chaque élément d'un ensemble. 

Vous ne voyez peut-être pas de quoi nous voulons parler en parlant d'ensembles. Pourtant, nous en avons déjà utilisé dans la partie précédente lorsque nous avons parlé des intervalles de nombres. Oui, c'est un ensemble. La boucle `for` nous permet alors d'effectuer des instructions pour chaque élément d'un intervalle.

Le code suivant exécute l'instruction `print n` et permet d'afficher tous les nombres de l'intervalle $[\![0, 5]\!]$:

```ruby
for n in 0..5
    print "#{n} " #instruction(s)
end
```

[[attention]]
| Nous devons encore le redire, le `end` est obligatoire.

Sans surprise, ce code affiche tous les nombres de l'intervalle $[\![0, 5]\!]$ :

```bash
0 1 2 3 4 5
```

Il existe une autre façon d'écrire des intervalles. Elle ressemble beaucoup à celle que nous avons déjà vu. En fait, pour l'utiliser, il suffit d'écrire `...` plutôt que `..`. Cependant, il y a une différence entre les deux syntaxes :

- `l..n` désigne l'ensemble des nombres entre $l$ et $n$, $l$ et $n$ inclus. 
- `l...n` désigne aussi l'ensemble des nombres entre $l$ et $n$, mais $n$ est cette fois exclu. 

Ainsi, le code 

```ruby
for n in 0...5
    print "#{n} " #instruction(s)
end
```

n'affichera que 

```
0 1 2 3 4
```

[[attention]]
| Notez que si dans la partie précédente, le `when` évaluait si le nombre proposé se trouvait dans 
| l'intervalle nombres réels compris, ici, l'intervalle est parcouru d'entiers en entiers. 

En y réfléchissant, ceci est tout à fait normal : si on commence à $2.3$ par exemple, comment savoir si on doit avancer de $1$ en $1$, ou si on doit par commencer à $2.3$ puis passer à $3$...

Nous verrons plus tard d'autres moyens de faire des itérations.

La boucle `for` peut également servir à parcourir une chaine de caractère. Dans ce cas, l'élément qui séparera les différents éléments de l'ensemble est le retour charriot `\n`. Ainsi, ce code nous affichera les trois mots séparés par un espace :

```ruby
for ligne in "zeste\nde\nsavoir"
  puts ligne
end
```