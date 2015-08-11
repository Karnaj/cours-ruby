# La console se ferme directement


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

# Le programme ne se lance pas
