Si vous êtes sous Linux, vous disposez sûrement déjà d'un éditeur de texte avec coloration syntaxique et support du langage Ruby. S'il s'agit d'un éditeur que **vous** avez choisi, que vous avez l'habitude d'utilisrr et qui vous convient, ne le changez pas. Sinon, vous devriez vous intéresser au large panel de choix qui est disponoble sous Linux. Il y en a vraiment pour tous les goûts. Ici, nous allons vous présenter Gedit, un éditeur de texte très simple, qui propose juste le peu de fonctionnalités dont nous avons actuellement besoin. Gedit utilise GTK.

# Installer gedit

Sur la plupart des distributions, gedit est installé par défaut. Il est par exemple fourni avec l'environnement de bureau GNOME. S'il n'est pas installé, il suffit d'utiliser votre gestionnaire de paquets pour l'installer. Par exemple :

```
sudo apt-get install gedit
pacman gedit
```

Vous savez quoi faire pour l'installer. Nous vous laissons faire. 

[[attention]]
| N'oubliez pas d'installer GTK pour obtenir Gedit avec la meilleure interface graphique.

Une fois Gedit installé, lancez le et habituez vous à l'interface. La coloration est choisie en fonction de l'extension du fichier ouvert (la coloration pour le Ruby est donc associée au fichier `rb`), mais vous pouvez bien sûr choisir la coloration dans les paramètres de Gedit.

# Exécuter le code

La façon la plus simple d'exécuter le script Ruby est d'utiliser le terminal : on ouvre un terminal, on se rend dans le dossier du script (à l'aide la commende `cd`) et on utilise la commande `ruby nom_du_script.rb`. Le fichier sera alors interprété par l'interpréteur Ruby, c'est à dire qu'il sera exécuté.

----

Vous pouvez bien sûr essayer d'autres éditeurs de texte. [Geany](www.geany.org/) par exemple offre plus de fonctionnalités tout en restant assez simple et ergonomique, mais choisissez avant tout un éditeur qui vous plaît et qui vous permet de coder facilement. Essayez en plusieurs, lisez les avis des autres, faîtes vous vos propres avis et choisissez le vôtre. 
