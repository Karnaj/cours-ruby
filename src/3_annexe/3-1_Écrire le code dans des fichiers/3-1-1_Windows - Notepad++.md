Sous Windows, l'éditeur de texte que nous allons vous présenter est Notepad++. Il s'agit d'un logiciel gratuit sous [licence GPL](zestedesavoir.com/articles/118/la-gpl-la-licence-des-cornus/). Il intègre la coloration syntaxique pour de nombreux langages et dispose de nombreuses extensions. 

# Installer Notepad++

Rien de plus simple ! Rendez-vous sur la [page de téléchargement](https://notepad-plus-plus.org/fr/download/v6.6.8.html) de Notepad++ puis cliquez sur le gros bouton vert ||Download||. Ensuite, suivez les instructions à l'écran comme pour un programme classique, rien de compliqué.

Voilà ! Notepad++ est installé sur votre ordinateur !

Notez que Notepad++ existe aussi en version portable. L'utilisation de la version portable d'un logiciel ne nécessite pas d'installation. Vous pouvez transporter cette version sur une clé USB et donc l'utiliser sur n'importe quel ordinateur avec vos paramètres. 

Pour obtenir la version portable de Notepad++, retournez sur la page de téléchargement du logiciel. Vous pourrez y trouver deux liens qui correspondent aux versions portables : « Notepad++ zip package» et « Notepad++ 7z package ». Au moment où nous écrivons, ces deux liens sont sous le bouton ||Download||.

# Exécuter le code

Pour lancer le code écrit, il suffit de l'enregistrer avec l'extension .rb puis de double-cliquer dessus.

##NppExec

Quoi ? On vient de me dire dans l'oreillette que c'est quand même fatigant de réduire Notepad++ puis double-cliquer sur votre fichier. Dans ce cas, voyons comment lancer le fichier avec un raccourci clavier. Pour cela nous allons utiliser une extension de Notepad++ appelé NppExec.

Pour commencer, installons NppExec. Cliquez sur `Compléments -> Plugin Manager -> Show Plugin Manager -> Available`. Là, cherchez NppExec, cochez-le et cliquez sur Install. 

![Installer NppExec](http://zestedesavoir.com/media/galleries/572/609f9453-8b71-49d9-81c3-d706e385fcdd.png.960x960_q85.png)
Figure : Installer NppExec

Maintenant que vous avez installé le plugin, il faut créer un script. Pour cela, appuyez sur ||F6|| (ou ||Fn + F6||) et tapez ceci: 

```
NPP_CONSOLE OFF                              // ne pas afficher la console NppExec
NPP_SAVE                                     // Sauvegarder le fichier courant
CD $(CURRENT_DIRECTORY)                      // Se placer dans le dossier du fichier courant
NPP_RUN cmd /c $(FULL_CURRENT_PATH) && pause // Exécuter le fichier puis mettre en pause la console
```

Cliquez sur `Save` et choisissez un nom pour votre script (pourquoi pas Ruby).

![Création du script](http://zestedesavoir.com/media/galleries/572/a6a47636-380a-42d1-91c3-6cd6775df351.png.960x960_q85.png)
Figure : Création du script

Cliquez sur `Compléments -> NppExec -> Advanced Options`. Choisissez le script que vous avez créé dans Associated script et cliquez sur Add/Modify.

![Ajout du script](http://zestedesavoir.com/media/galleries/572/7567f103-6a71-4f16-aa63-46cca129f319.png.960x960_q85.png)
Figure : Ajout du script

Il ne nous reste plus qu'à faire un raccourci clavier pour ce script: cliquez sur Paramétrage -> Raccourcis clavier... -> Plugin commands, cherchez le nom du script, double-cliquez dessus (ou cliquez sur Modify) et choisissez un raccourci (F9 est souvent utilisé mais la seule règle à respecter est de ne pas utiliser des touches déjà utilisées. Ctrl + Alt + R peut être une bonne idée).

![Ajout du raccourci](http://zestedesavoir.com/media/galleries/572/7bf05dea-c1ab-442f-9e7f-3c0e354c3aa6.png.960x960_q85.png)
Figure : Ajout du raccourci

Ça y est, vous avez votre super raccourci (notez que vous pouvez utiliser le même raccourci pour Python par exemple).