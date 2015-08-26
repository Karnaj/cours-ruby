# Qu'est-ce qu'un objet

Jusqu'à présent, vous avez entendu parler d'objets (notamment dans l'appellation *programmation orientée objet*). Il est temps pour nous d'expliquer ce que c'est. Un objet peut tout simple être vu comme une structure de données (un *agrégat* comme on dit) qui existe par lui-même (un objet est une variable) et qui contient des **attributs** (des sous-variables en sommes). Il est possible de manipuler un objet au travers de mécanismes prévus pour. Ces mécanismes se trouvent être des fonctions bien particulières qu'on nomme **méthodes**.

Afin d'illustrer ce qui vient d'être dit, on va utiliser l'exemple d'un bête point (géométrique). Un point existe en lui-même, on peut le manipuler tel quel, le nommer. Il a des attributs, ses coordonnées (disons x et y). On peut aussi lui affecter des méthodes (une méthode pour calculer la distance entre celui-ci et un autre point, par exemple) :

```text
Point :
  attributs :
    x (entier)
    y (entier)
  méthodes :
    distance(autrePoint), renvoie un flottant
```

# Une affaire de vocabulaire

Maintenant que nous savons ce qu'est un objet, il faut comprendre comment ils sont représentés en Ruby. Chaque objet appartient à une classe. Tout comme on dit qu'une variable a un type, un objet appartient à une classe. **C'est le même principe** (en fait les types des variables sont en fait des classes). Ainsi, pour pouvoir créer des points, il nous faudrait créer des variable de type *Point* (où *Point* serait la classe qui définit structurellement un point).

Une classe est donc un moule, un plan qui permet de construire des objets de cette classe. On donne à ce moule des caractéristiques particulières (typiquement les variables et les méthodes) ce qui nous permet, en utilisant ce moule, d'obtenir des objets appartenant à la classe désirée. On ne manipule pas la classe mais des objets de cette classe. On utilise la classe pour créer de nouveaux objets. 

Lorsqu'on crée un objet, on dit qu'on crée une nouvelle **instance** de la classe (ou qu'on **instancie** la classe).  

[[information]]
| La création de classe faisant l'objet d'un autre chapitre, nous nous intéresserons pour l'instant à des classes préexistantes et la création d'objets à partir de ces classes (**l'instanciation**).
