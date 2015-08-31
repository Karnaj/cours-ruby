Avant de coder en Ruby, il va de soi qu'il faut l'installer.

Heureusement, nous allons vous expliquer pas à pas comment faire.

[[information]]
| Il y a plusieurs façons d'installer Ruby, elles sont détaillées sur [cette page](https://www.ruby-lang.org/fr/downloads/). Nous allons ici vous montrer la plus simple.

# Installation sous Windows

Pour commencer, téléchargez la dernière version de RubyInstaller sur [cette page](http://rubyinstaller.org/downloads/).

![Capture du site RubyInstaller](/media/galleries/572/cd437911-ea31-431a-969f-364e25008c06.jpg.960x960_q85.jpg)
Figure : Capture du site

Ensuite, il vous suffit d’exécuter l'installateur téléchargé.
Cliquez sur Suivant - Suivant - Installer en prenant soin de cocher les cases comme ci-dessous.

![Exécutable](http://zestedesavoir.com/media/galleries/572/875c81c0-b79e-41a3-b494-b4fab7e04350.png.960x960_q85.jpg)
Figure : Exécutable

# Installation sous Linux

Ruby est déjà installé sur certaines distributions. Pour savoir s'il est déjà installé sur votre ordinateur, utilisez la commande `ruby`. Si elle ne vous renvoie pas d'erreur, alors Ruby est installé (Notez également la commande `ruby -v` qui renvoie le numéro de version). 

Si Ruby n'est pas encore installé, le plus simple est d'utiliser votre gestionnaire de paquets pour l'installer.  

```
$ sudo apt-get install ruby-full
$ sudo pacman -S ruby
```

# Installation sous OS X

Nous avons de la chance, depuis quelques versions, Ruby est installé de base su OS X. Vous n'avez donc rien à faire. Vous devez juste lancer la commande `ruby -v` dans votre terminal pour connaître la version qui est installé. 

---

Félicitation !
Ruby est maintenant installé sur votre ordinateur. Nous allons maintenant apprendre à l'utiliser.
