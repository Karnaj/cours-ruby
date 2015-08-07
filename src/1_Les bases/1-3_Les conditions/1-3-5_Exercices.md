Voilà une nouvelle série d'exercices juste pour vous.

# Exercice 1

Le premier exercice est encore une fois plutôt simple : demandez à l'utilisateur d'entrer trois nombres et affichez le plus grand des trois nombres.

Correction :

[[secret]]
| Voici notre correction. Votre code peut bien sûr être différent. On a été malin. On compare le nouveau 
| nombre rentré au maximum des nombres déjà rentré. 
|
| ```ruby
| nombre = gets.chomp.to_i
| max = nombre
| nombre = gets.chomp.to_i
| max = nombre if nombre > max
| nombre = gets.chomp.to_i
| max = nombre if nombre > max
| print max
|```

Maintenant, modifiez ce programme pour qu'il affiche les trois nombres triés par ordre croissant.

Correction :

[[secret]]
| Pour faire cela, nous allons demander nos trois nombres et les trier dans l'ordre, et les afficher ensuite.
| 
| ```ruby
| nombre1 = gets.chomp.to_i
| nombre2 = gets.chomp.to_i
| nombre3 = gets.chomp.to_i 
| if nombre1 > nombre2 # si nombre1 > nombre2, on les échange
|    tmp = nombre1
|    nombre1 = nombre3
|    nombre3 = tmp
| end
| if nombre2 > nombre3 # si nombre2 > nombre3, on les échange
|    tmp = nombre2
|    nombre2 = nombre3
|    nombre3 = tmp
|    # ancien_nombre2 était plus grand que ancien_nombre2, alors il peut être plus grand que nombre1
|    if nombre1 > nombre2 
|       tmp = nombre1
|       nombre1 = nombre2
|       nombre2 = tmp
|    end
| end
| puts nombre1, nombre2, nombre3 
| ```
| 
| Si vous ne comprenez pas l'idée qui est mise en place prenez un papier et un crayon. 

# Exercice 2

Cet exercice est plus un mini TP. Vous devez demander une année à l'utilisateur et déterminer si elle est ou non bissextile. Donc, il vous faut savoir la condition suivant laquelle une année peut être qualifiée de bissextile.

[[information]]
| Une année est dite bissextile si elle est divisible par $400$ ou si elle est divisible par $4$ et non 
| divisible par $100$.

 Aide :

[[secret]]
| Vous devez vous poser une question : comment tester si un nombre `a` est multiple d'un nombre `b` ?  
| Il suffit, en fait, de tester le reste de la division entière de `b` par `a`. Si ce reste est nul, alors a | est un multiple de b :
|
| ```ruby
| 5 % 2 # 5 n'est pas un multiple de 2
| => 1
| 8 % 2 # 8 est un multiple de 2
| => 0
| ```
|
| Il suffit d'appliquer cette méthode à notre cas. :soleil:

Si vous avez regardé l'aide, ça devrait aller maintenant. Lancez vous et vous y arriverez !

Correction :

[[secret]]
|Inutile de sauter sur la correction, cela ne sert à rien !  
|
| Voici la nôtre (votre code peut parfaitement être différent mais fonctionner de la même manière) :
|
| ```ruby
| puts "Entrez une annee : "
| annee = gets.chomp()
| annee = annee.to_i()
| if annee % 400 == 0
|    puts "L'annee est bissextile."
| elsif annee % 4 == 0 && annee % 100 != 0
|    puts "L'annee est bissextile."
| else
|   puts "L'annee n'est pas bissextile."
| end
| ```
|
| On peut le simplifier :
| 
| ```ruby
| puts "Entrez une annee : "
| annee = gets.chomp()
| annee = annee.to_i()
| if annee % 400 == 0 or (annee % 4 == 0 && annee % 100 != 0)
|    puts "L'annee est bissextile."
| else
|    puts "L'annee n'est pas bissextile."
| end
|```

# Exercice 3

Nous allons maintenant devenir commerçants. Votre objectif : vous devez demandez à l'utilisateur de rentrer le prix HT d'un objet et son code (compris entre $1$ et $3$) et calculer le prix TTC de l'objet sachant que le code $1$ correspond à une TVA de $20\%$le code $2$ à une TVA de $10\%$ et le code $3$ à une TVA de $5.5\%$ (on considère que la seule taxe est la TVA). 

Vous allez donc devoir manier des pourcentages.

Correction :

[[secret]]
| On va déclarer trois constantes correspondant aux trois taux des TVA et les utiliser pour nos calculs. 
|
| ```ruby
| TVA1 = 20.0
| TVA2 = 10.0
| TVA3 = 5.5 
| 
| print "Entrez le prix de votre produit : "
| prixHT = gets.chomp.to_f
| print "Entrez le code de votre produit : "
| code = gets.chomp.to_i
|
| if code == 1
|    prixTTC = prixHT + TVA1 / 100 * prixHT   
| elsif code == 2
|    prixTTC = prixHT + TVA2 / 100 * prixHT 
| elsif code == 3
|    prixTTC = prixHT + TVA3 / 100 * prixHT
| end
|   
| case code
|    when 1..3
|       print "Le prix TTC de votre produit est #{prixTTC}"   
|    else
|       print "Votre code n'est pas valide"
| end
| ```
| 
| Le code peut être raccourci par exemple de cette manière :
|
| ```ruby
| print "Entrez le prix de votre produit : "
| prixHT = gets.chomp.to_f
| print "Entrez le code de votre produit : "
| code = gets.chomp.to_i
| 
| if code == 1
|    print "Le prix TTC de votre produit est #{prixHT * 1.2}"   
| elsif code == 2
|    print "Le prix TTC de votre produit est #{prixHT * 110 / 100}" 
| elsif code == 3
|    print "Le prix TTC de votre produit est #{prixHT * 105.5 / 100}"
| else
|    print "Votre code n'est pas valide"
| end
| ```

*[HT]: Hors-taxe
*[TTC]: Toute taxe comprise
*[TVA]: Taxe sur la valeur ajoutée