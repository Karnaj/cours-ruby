# Irb

Ruby possède ce que l'on appelle un environnement interactif, ici appelé irb. 
Irb interprète votre code au fur et à mesure que vous l'écrivez : vous entrez une instruction et vous appuyez sur ||Entrée||, cette instruction est alors exécutée.

[[information]]
| Pour lancer irb, il faut passer par l'invite de commande (Shell sous Linux et Terminal.app sous OS X). 
| Sous Windows, il suffit de taper cmd dans la barre de recherche du menu démarrer.
| L'invite de commande maintenant ouverte, tapez irb. Vous avez maintenant une magnifique console qui
| interprète ce que vous écrivez en Ruby.

En lançant irb, vous vous retrouvez face au symbole `>`. Ce chevron signifie une chose : irb est vos ordres et il attend vos instructions. Lorsqu'il vous « répond », sa réponse est située après le signe `=>` sur une nouvelle ligne. Tapez `2` par exemple, vous verrez qu'il vous répondra `2` (oui, il répond bien `2`).

```
> 2
=> 2
```

[[attention]]
| En Ruby, les instructions sont séparés par un point-virgule. Celui-ci peut cependant être omis s'il n'y a 
| qu'une instruction par ligne.

Ainsi, nous pouvons écrire cela :

```ruby
3; 2    
```

Mais ceci ne fonctionnera pas et vous obtiendrez une belle erreur :

```ruby
3 4
```

Nous vous conseillons alors de ne mettre qu'une seule instruction par ligne.

Pour quitter Irb, vous devez entre `quit` et valider.

# Opérations mathématiques

Les premières instructions que nous allons voir sont les opérations mathématiques. Irb fonctionne comme une calculatrice et vous donne le résultat juste en dessous. Il respecte même les priorités (avec ou sans parenthèses). Essayez d'écrire des opérations mathématiques. Vous devriez obtenir quelque chose de ce genre : 

```
> 3 + 2
=> 5
> 2 * 3 + 5
=> 11
> (2 * 3) + 5
=> 11
> (6 - 2)*(8 + 25)
=> 132
```

Vous pouvez même assigner des valeurs à une lettre pour effectuer des opérations sur celle-ci.

```
> x = 4
=> 4
> y = 7
=> 7
> x + y
=> 11
```

[[attention]]
| Essayez les divisions. L'invite donne toujours un résultat entier : par exemple, `5 / 3 = 1`.

Nous allons voir quel est le problème de la division. Mais avant cela, voici un tableau des opérations mathématiques que nous avons vu :  

Action  |   Code  |  Affichage
------|------|------
Additionner |   3 + 2  |  Affiche 5
Soustraire |   3 - 2  |  Affiche 1
Multiplier |   3 * 2  |  Affiche 6
Diviser | 3 / 2  |  Affiche 1
Modulo | 3 % 2  | Affiche 1 (le reste de la division euclidienne)

Nous pouvons également y ajouter l'opération **puissance** qui s'utilise avec `**`. En tapant `2 ** 2`, on obtient donc `4`. 

## Un peu de sucre syntaxique

L'expression [sucre syntaxique](https://fr.wikipedia.org/wiki/Sucre_syntaxique) désigne des parties d'un langage de programmation qui permettent d'écrire et de lire du code plus facilement. À ce niveau du cours, nous n'avons pas encore de quoi voir du sucre syntaxique, mais il existe des raccourcis aux opérateurs mathématiques que l'on peut considérer comme du sucre syntaxique. 
  
Prenons l'exemple d'une variable `variable` qui vaut $4$. On veut la multiplier par $3$. Le code qui s'impose est :

```
variable = 4
variable = variable * 3
```

Ceci est parfaitement correct. Cependant, on peut raccourcir cette écriture en écrivant

```C
variable = 4
variable *= 3
```

Et cette syntaxe ne marche pas que pour la multiplication. Voici un tableau des opérations et de leurs équivalents :

+------------------------------+--------------------+  
|          Opérations          |     Équivalent     |  
+==============================+====================+      
| variable = variable + nombre | variable += nombre |  
+------------------------------+--------------------+     
| variable = variable - nombre | variable -= nombre |  
+------------------------------+--------------------+  
| variable = variable * nombre | variable *= nombre |  
+------------------------------+--------------------+  
| variable = variable / nombre | variable /= nombre | 
+------------------------------+--------------------+     
| variable = variable % nombre | variable %= nombre |  
+------------------------------+--------------------+  

# Entiers et flottants

En voyant ce que sont les entiers et les flottants, nous verrons qu'en fait, le résultat que nous obtenons avec la division n'est pas une erreur.

On appelle un entier un nombre comme $3$, $37$ ou $-12$. Un flottant est un nombre avec une partie décimale comme $5$, $6$ ou $32,5$. Les flottants sont donc les nombres qui ne sont pas entiers.

Revenons à notre problème. Celui-ci est directement lié aux notions d'entiers et de flottants : En fait, quand on tape `3 / 2`, on divise deux entiers. Le résultat est donc aussi un entier. En toute logique, pour obtenir un résultat à virgule (donc un flottant), il faut diviser deux flottants. Donc pour obtenir le résultat attendu, il nous aurait fallu taper `3.0 / 2.0`. Tapez `3.0 / 2.0` dans irb, et admirez le résultat.

[[attention]]
| Vous l'avez remarqué. Pour écrire un nombre décimal, on utilise la notation anglo-saxonne. Il faut donc 
| utiliser un point et non une virgule ! De plus, nous sommes obligés de rajouter la partie décimale même si
| elle est nulle pour préciser qu'on utilise un flottant.

Si vous voulez additionner deux nombres, le premier un entier et le second un flottant, le résultat sera un flottant. Ainsi, en tapant `2 + 3.5`, on obtient bien `5.5`. La conversion est faite implicitement.

Faites des essais, regardez les résultats des calculs et habituez vous à les utiliser. Vous en aurez besoin au prochain chapitre !

*[irb]: Interactive Ruby