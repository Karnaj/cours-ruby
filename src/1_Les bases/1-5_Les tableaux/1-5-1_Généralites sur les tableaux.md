# Qu'est-ce qu'un tableau

C'est l'heure pour nous de voir les tableaux. Un tableau est une super variable. En fait, c'est une structure de données. Cette structure est un ensemble d'éléments ordonnées auxquels on peut accéder par un indice, d'où le nom « tableau ». Les tableaux sont des variables qui contiennent d'autres variables. Ce sont donc des « séquences » d'éléments tout comme les intervalles `n..l` vu dans le chapitre précédent. 

[[information]]
| Le premier indice d'un tableau est l'indice $0$ et non $1$. 

On a donc l'élément d'indice $0$, l'élément d'indice $1$... On peut alors voir un tableau comme une variable qui contient d'autres variables tout simplement. 

Un tableau permet alors de rassembler des informations. Par exemple, vous pourriez vouloir les âges de cinquante personnes. Récupérer ces cinquante âges dans un tableau peut être judicieux. 

En effet, les tableaux permettent d'agir très facilement sur l'ensemble des éléments, et en continuant avec l'exemple des cinquante âges, vous pourriez multiplier tous ces âges par deux en moins de dix lignes en utilisant un tableau alors qu'avec cinquante variables vous auriez besoin de cinquante lignes. 
   
Les tableaux permettent donc de s'affranchir de beaucoup de contraintes (et de copier-coller) et favorisent le développement.   

Et pour mettre un mot sur les choses, il nous faut préciser que les tableaux sont ce que l'on appelle un **[conteneur](https://fr.wikipedia.org/wiki/Conteneur_(informatique))**.
 
# Déclarer un tableau

Pour déclarer un tableau, nous devons utiliser les crochets `[]`. Cela permet de déclarer un tableau vide.

```ruby
tab = []
``` 

Pour afficher le tableau, nous pouvons utiliser la méthode `print` comme d'habitude. 

```ruby
tab = []
print tab
```

On affiche `tab`, on obtient « $[]$ », le tableau vide.

Les éléments du tableau sont placés entre les crochets, séparés par des virgules. Voici comment déclarer le tableau contenant les éléments $1$, $2$, et $3$.

```ruby
tab = [1, 2, 3]
print tab
```

On obtient cette fois cet affichage : « $[1, 2, 3]$ ». 

[[information]]
| Les crochets ne sont pas obligatoires. Vous pouvez ne pas les utiliser et juste séparer les éléments par 
| des virgules. Cependant, ils sont obligatoires dans le cas où il y a moins de deux éléments.

Ainsi, nous aurions pu parfaitement faire notre dernier exemple de cette manière :

```ruby
tab = 1, 2, 3
print tab
```

Cependant, pour des raisons de compréhension, nous vous conseillons de toujours utiliser les crochets. 

Maintenant, vous pouvez faire des tableaux d'entiers, des tableaux de flottants et même des tableaux de chaines de caractères. C'est bien, mais il y a mieux : en Ruby, les tableaux mixtes sont possibles. Cela veut dire que vous pouvez parfaitement faire un tableau contenant des entiers **et** des chaines de caractères voire même d'autres tableaux. Ce code est parfaitement valide :

```ruby
tab = [3.23, "Trois virgule vingt-trois", [3, '.', 2, 3]]
print tab
```