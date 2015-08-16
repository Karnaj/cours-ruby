# Voir les erreurs obtenus

Vous ne l'avez peut-être pas encore remarqué, mais écrivez un code erroné et essayez de l'exécuter en cliquant sur le fichier
ou en utilisant les méthodes ci-dessus. Exécutez par exemple ce code tout simple :

```ruby
a = "Hello""
```

Problème, la console s'ouvre et se referme aussitôt et nous n'avons pas le temps de voir l'erreur. Ici pas de problème, nous 
avons délibérément fait une erreur, mais imaginez dans un code de plusieurs centaines de lignes où une petite erreur s'est glissée.
Si on n'a pas accès à l'erreur, la régler sera très compliquée et demandera de relire tout le code. Il nous faut donc faire en 
sorte que la console ne se ferme pas.

Pour cela, nous allons donc utiliser un peu la console. La seule commande de la console que vous devez connaître est la commande
`cd` (pour change directory) qui permet de changer de répertoire. Voici ce que nous allons faire :

- ouvrir une console
- se rendre dans le dossier de notre fichier `rb`
- exécuter notre fichier `rb`

Ouvrir une console, vous savez faire. Pour vous rendre dans le dossier, nous allons utiliser la commande `cd`. Supposons que nous 
soyons dans le dossier `/home/user/` au démarrage de la console et que notre fichier qui s'appelle `test.rb` est dans le dossier
`/home/user/programmation/ruby`. Il nous faudra alors taper `cd programmation/ruby`, puis `test.rb`. On peut aussi, le faire en 
plus d'étapes en tapant :

```
cd programmation
cd ruby
test.rb
```

[[attention]]
| La commande `cd` est une commande bash. Elle n'est donc pas à utiliser dans irb, mais directement dans la console. 

# La console se ferme directement

Si en cliquant sur le programme, la console se ferme directement, c'est tout à fait normal, notre programme s'exécute, pui se ferme. Pour qu'il reste ouvert, nous avons deux solutions :

- utiliser la méthode du point précédent et ouvrir le programme en passant par la console (utiliser `cd` pour se rendre dans le dossier et l'exécuter)
- demander au programme d'attendre par exemple une saisie de l'utilisateur

Nous avons déjà vu la première méthode, voyons maintenant la seconde. Elle n'est pas beaucoup plus compliquée (en fait, elle est même plus simple), il suffit d'utiliser `gets` à la fin de notre code. Comme cela, le programme attendra une saisie de l'utilisateur et se fermera dès qu'il l'utilisera. Par exemple :

```ruby
a = "Bonjour"
gets
```

[[attention]]
| Utiliser `gets` ne fonctionne pas dans le cas d'un code eronné. En effet, dès que Ruby encontre une erreur dans le programme
| , il l'arrête. 

Ainsi, pour corriger les erreurs de votre code par exemple, il vaut mieux se déplacer dans le dossier de votre programme à l'aide de `cd` et exécuter le programme pour trouver les erreurs. 

Utilisez `gets` par exemple lorsque vous avez fini un programme et que vous voulez pouvoir l'utiliser directement (ou le passer un ami). Pour le moment, nous ne sommes pas dans ce cas et n'avons pas le niveau de faire des programmes nécessitant cela, mais dans quelques temps, nous pourrons déjà faire des petits scripts intéressants.


# Le programme ne se lance pas

Il peut aussi arriver que lorsque vous cliquiez sur le programme (ou l'exécutiez grâce au script de Notepad++ par exemple), celui-ci ne se lance pas ou encore que le fichier s'ouvre avec votre éditeur de texte ou un autre programme. Cela signifie tout simplement que le programme avec lequel les fichiers `rb` sont lancés n'est **pas** Ruby. Pour régler cela, il vous suffit donc de choisir l'interpréteur Ruby en tant que programme par défaut.  

Cependant, il peut arriver que vous vouliez justement que le programme s'ouvre par défaut avec votre éditeur. Dans ce cas, lorsque vous voulez lancer le programme, il faut indiquer à votre ordinateur que vous voulez le lancer avec l'interpréteur Ruby. S'il s'agit de le lancer en cliquant dessus, les OS ont toujours une option `Ouvrir avec` accessible depuis un clic droit. Si vous voulez le lancer depuis la console, il faut alors utiliser la commande `ruby nom_du_fichier.rb` plutôt que `nom_du_fichier.rb` pour lancer le fichier avec Ruby. De même, il faudra alors changer nos scripts et indiquer que le fichier est à ouvrir avec Ruby. Ainsi, la dernière ligne du script de NppExec devient `NPP_RUN cmd /c ruby $(FULL_CURRENT_PATH) && pause`.
