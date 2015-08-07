# Exercice 1

Voici le premier exercice : faire une calculatrice ! Vous devez gérer les quatre opérations usuelles : l'addition, la soustraction, la multiplication et la division. L'utilisateur devra choisir une opération, puis saisir deux nombres. Vous afficherez le résultat de l'opération. Voici un exemple de ce que doit afficher votre programme :

```
Choisissez une opération :

1. Addition
2. Soustraction
3. Multiplication
4. Division

Votre choix : 3

Vous avez choisi la Multiplication. 

Entrez le premier nombre : 4
Entrez le second nombre : 23

4.0 * 23.0 = 92
```

Correction :

[[secret]]
| ```ruby
| def menu 
|    tab = ["Addition", "Soustraction", "Multiplication", "Division"]
|    for i in 0..3
|       puts "#{i + 1} #{tab[i]}"
|    end
|    choix = 0
|    while choix < 1 or choix > 4
|       print "\nVotre choix : "
|       choix = gets.chomp.to_i
|    end
|    puts "\nVous avez choisi la #{tab[choix - 1]}"
|    return choix
| end
| 
| choix = menu
| print "\nEntrez le premier nombre: "
| nombre1 = gets.chomp.to_f
| print "Entrez le second nombre: "
| nombre2 = gets.chomp.to_f
| puts
| if choix == 1
|    print "#{nombre1} +  #{nombre2} =  #{nombre1 + nombre2}"
| elsif choix == 2
|    print "#{nombre1} -  #{nombre2} =  #{nombre1 - nombre2}"
| elsif choix == 3
|    print "#{nombre1} *  #{nombre2} =  #{nombre1 * nombre2}"
| elsif nombre2 != 0
|    print "#{nombre1} /  #{nombre2} =  #{nombre1 / nombre2}"
| else
|    print "Diviser par 0 c'est mal"
| end
| ```

# Exercice 2

Exercice un peu plus difficile cette fois. Votre programme doit demander deux nombres à l'utilisateur et afficher le PGCD de ces deux nombres. Je vous propose de faire un tour sur [la page Wikipédia du PGCD](http://fr.wikipedia.org/wiki/Plus_grand_commun_diviseur) pour vous rafraîchir la mémoire.

Correction :

[[secret]]
|
| ```ruby
| def pgcd(a, b)
|    if a > b
|       tmp = a
|       a = b
|       b = tmp
|    end
|    if a == 0
|       return b
|    end
|    while b % a != 0
|       tmp = b % a
|       b = a
|       a = tmp
|    end
|    return a
| end
| ```

# Exercice 3

Nous allons finir par faire un convertisseur. Vous devez demander à l'utilisateur de choisir une conversion et afficher le résultat de cette conversion. Voici les conversions que la première version de votre programme doit gérer (dans les deux sens bien sûr) :

- conversion de degrés en radians ($1$ degré = $\dfrac{180}{\pi}$ radians
- passage de km/h à m/s ($1$ m/s = $3.6$ km/h)

Ces deux conversions sont très utiles en physique. Vous devez également réaliser un menu dans lequel vous proposerez à l'utilisateur de réaliser une des conversions ou de quitter le programme.

Correction :

[[secret]]
| Le but des fonctions est d'avoir un code bien découpé. Utilisons les donc pour avoir un beau programme (en
| (plus, c'est un peu le but vu le nom du chapitre).
|
| ```ruby
| def menu 
|    puts "1. Convertir des radians en degrés"
|    puts "2. Convertir des degrés en radians"
|    puts "3. Convertir des kilomètres par heures en mètres par seconde"
|    puts "4. Convertir des mètres par seconde en kilomètres par heures"
|    puts "5. Quitter"
|    choix = 0
|    while choix < 1 or choix > 5
|       print "\nVotre choix : "
|       choix = gets.chomp.to_i
|    end
|    return choix
| end
| 
| PI = 3.14159265359
| DEG_VERS_RAD = PI / 180 
| MS_VERS_KMH = 3.6
| choix = menu
| if choix != 5
|    print "\nEntrez le nombre: "
|    nombre = gets.chomp.to_f
|    if choix == 1
|       print nombre / DEG_VERS_RAD
|    elsif choix == 2
|       print nombre * DEG_VERS_RAD
|    elsif choix == 3
|       print nombre / MS_VERS_KMH
|    else
|       print nombre * MS_VERS_KMH
|    end
| end
| ```

Maintenant que vous avez réalisé ce programme, vous pouvez le compléter en rajoutant quelques autres conversions :

- conversion de pieds en mètres ($1$ pied = $0.3048$ mètres)
- conversion de grammes en livres ($1$ gramme = $0.002205$ livres)
- conversion de degrés Fahrenheit en degrés Celsius (Température en degrés Fahrenheit = $32 + 1.8 \times$ Température en degrés Celsius). 
- conversions de diverses devises (euro dollar livres...)

Vous pouvez même (et nous vous le conseillons en guise d'entraînement) faire un programme de conversions d'un nombre vers un autre base. Gérer le binaire, l'octal, le décimal et l’hexadécimal est suffisant pour commencer, mais votre programme devrait à terme être capable de convertir un nombre de n'importe quelle base en n'importe quelle autre base. 

Encore une fois, n'hésitez pas à faire un tour sur les [forums](http://zestedesavoir.com/forums/savoirs/programmation/) si vous êtes coincés, et envoyez-nous vos codes par MP !