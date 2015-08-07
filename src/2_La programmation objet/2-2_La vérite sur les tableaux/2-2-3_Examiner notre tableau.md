Il existe aussi quelques méthodes dans la classe *Array* qui sert à examiner un tableau (connaitre le nombre d'éléments, savoir s'il est vide...). En voici quelques unes :

- `any?` : Renvoie *True* si le tableau n'est pas vide, *False* sinon
- `any? {block}` : Renvoie *True* s'il existe au moins un élément pour lequel le bloc renvoie *True*
- `empty?` : Contraire de `any?` (pas de version avec bloc !)
- `include?(object)` : Renvoie *True* si le tableau contient *object*
- `length` ou `size` : Renvoie la taille du tableau
- `count` : Renvoie la taille du tableau
- `count(obj)` : Renvoie le nombre de fois où *obj* apparait
- `count {block}` : Renvoie le nombre d'éléments pour lesquels le bloc renvoie *True*
- `fetch(index)` : Renvoie l'élément à l'indice *index*