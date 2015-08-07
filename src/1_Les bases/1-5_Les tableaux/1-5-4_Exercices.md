# Exercice 1

Ce premier exercice va vous faire travailler les boucles et les tableaux. Vous devez demander à l'utilisateur combien de cases il veut pour un tableau, le nombre maximum de cases étant de $10$ (vous pouvez soit lui redemander un nombre de cases, soit choisir $10$ par défaut si il ne donne pas un nombre valide). Vous devez ensuite lui demander les valeurs de son tableau. Et enfin, vous devez afficher ceci pour chaque valeur du tableau « Votre tableau contient (la valeur en question ici) ». Un exemple :

```
Combien de cases (entre 1 et 10) : 2

Entrez un nombre : 2
Entrez un nombre : 4

Votre tableau contient 2
Votre tableau contient 4 
```

Correction :

[[secret]]
| Nous décidons de lui redemander tant que la valeur entrée n'est pas bonne.
| 
| ```ruby
| nombre = 0
| while nombre > 10 or nombre <= 0 
|    print "Combien de cases (entre 1 et 10) :"
|    nombre = gets.chomp.to_i
| end
| puts
| 
| tab = []
| for i in 1..nombre
|    print "Entrez un nombre :"
|    a = gets.chomp.to_i
|    tab << a # On rajoute l'élément au tableau
| end
| puts
| 
| tab.each do |element|
|    print "Votre tableau contient #{element} \n"
| end
| ```

# Exercice 2

Maintenant, manipulons plusieurs tableaux. Votre programme doit afficher les valeurs de deux tableaux de même taille dans l'ordre croissant (les deux tableaux sont déjà triés à l'origine). Si une valeur est présente dans les deux tableaux, vous ne devrez l'afficher qu'une seule fois. Vous pourrez demander à l'utilisateur de vous donner des valeurs pour créer votre tableau.   

Correction :

[[secret]]
| Pour faire cet exercice, parcourir les tableaux à l'aide de leurs indices peut être astucieux. Regardez :  
|
| ```ruby
| tab1 = [-3, 0, 5, 12, 23]
| tab2 = [-2, 1, 2, 3, 8]
| n = 5
| i = 0
| j = 0
| while i < 5 or j < 5
|    if j == 5 or tab1[i] < tab2[j] 
|       print "#{tab1[i]} "
|       i = i + 1
|    else
|       print "#{tab2[j]} "
|       j = j + 1
|    end
| end
| ```
|
| La seule chose qui pourrait vous déboussoler est le `if j == 5`. Ici, on vérifie la valeur de $j$ pour 
| rester dans le tableau. Déroulez l'algorithme à la main sur un papier si nous ne le comprenez pas bien. 

# Exercice 3

En troisième exercice, nous allons faire un petit exercice de compression. Vous devez demander à l'utilisateur une chaine de caractère composée de $1$ et de $0$ et afficher le résultat de la compression (ce résultat doit être tableau). Voici comment nous allons procéder pour la compression : nous représenterons $n$ chiffres $1$ d'affilée par « $n1$ » et ferons de même pour les $0$. Voici un exemple :

```
Entrez la chaine à compresser : 110000111000110
Résultat : 214031302110
```   

Vous avez de quoi bien travailler.

Correction :

[[secret]]
|
|
| ```ruby
| print "Entrez la chaine à compresser : "
| chaine = gets.chomp 
| 
| actuel = chaine[0]
| nombre = 0
| tab = []
| chaine.each_char do |caractere|
|    if caractere == actuel
|       nombre = nombre + 1
|    else
|       tab << nombre
|       tab << actuel
|       actuel = caractere
|       nombre = 1
|    end
| end
| tab << nombre
| tab << actuel
| print tab
| ```
|
| Ce que nous avons fait fonctionne avec des $1$ et des $0$, mais aussi avec n'importe quel autre caractère.