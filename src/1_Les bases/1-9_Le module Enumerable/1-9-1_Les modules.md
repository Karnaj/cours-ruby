# Les modules

Un module est un genre de structure regroupant à la fois des variables et des méthodes. Cependant, **un module n'est pas une variable**.
En effet, un tableau contient lui aussi des variables et des méthodes, mais ce n'est pas pour autant un module.

Un module permet de partager du code avec d'autre structure du langage, comme d'autres modules, 
ou encore des *classes* (mais nous aborderons ces choses la dans la prochaine partie).
Cela permet de réduire le nombre de ligne de code à écrire, et de coller au principe *DRY (Don't repeat yourself)*. 
En effet, il n'est pas utile de réécrire deux fois la même fonction ! 
Les créateurs de Ruby le savent bien, et c'est pourquoi les **tableaux** et les **hash** utilisent un même module : le fameu module `Enumerable`.	

Pour info, un module se construit de cette façon :

``` ruby
module MonModule
  MA_CONSTANTE = 5
  
  def une_fonction
	  
  end
  
  def MonModule.une_fonction_statique
	  
  end
end
```

Mais ce n'est pas ce qui va nous interresser dans ce chapitre.