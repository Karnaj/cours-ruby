Sous OS X, vous disposez aussi de plusieurs éditeurs de texte. Un très bon éditeur est TextWrangler. Il s'agit tout comme Notepad++ d'un éditeur gratuit, mais il est sous licence propriétaire. TextWrangler est très utilisé, alors vous êtes sûr d'obtenir de l'aide si vous avez un problème.

TextWrangler est le petit frère gratuit de BBEdit. Ils sont tous deux édités par *Bare Bones* et si TextWrangler dispose de moins de fonctionnalités, il est largement suffisant pour nous. Vous pouvez voir les différences entre les deux logiciels [ici](http://www.barebones.com/products/bbedit/comparison.html) sur le site de l'éditeur (en anglais).

# Installer TextWrangler

Pour télécharger TextWrangler, vous pouvez tout simplement aller sur le Mac App Store, le rechercher et l'installer (lien direct de l'aperçu de l'application, permettant d'accéder sur la page correspondante du Mac App Store pour les habitants de France : [https://itunes.apple.com/fr/app/textwrangler/id404010395?mt=12](https://itunes.apple.com/fr/app/textwrangler/id404010395?mt=12)).

Néanmoins, les mesures de sécurité imposées par Apple au Mac App Store (voir l'article [Sandbox (sécurité informatique)](https://fr.wikipedia.org/wiki/Sandbox_(sécurité_informatique)) sur Wikipédia) ne permettent pas au logiciel d'accéder à des dossiers tels que `\etc`, n'appartenant pas à l'utilisateur courant. De même, le logiciel obtenu à partir du Mac App Store n'installe pas des outils supplémentaires en ligne de commande.

C'est pourquoi nous recommandons aux utilisateurs avancés de le télécharger directement sur le [site de l'éditeur](http://www.barebones.com/products/textwrangler/). Le lien est, au moment où nous écrivons, dans le menu à droite. Il suffit de cliquer sur le bouton ||Download Now|| pour obtenir la dernière version disponible. Vous obtiendrez un fichier `dmg`. En double-cliquant sur ce fichier, vous le monterez (en fait c'est une image disque) et vous pourrez exécuter le logiciel, après l'avoir installé sur le disque dur, de préférence dans le dossier Applications, ce qui est réalisé très simplement en faisant glisser l'icône de gauche sur l'icône de droite, comme indiqué dans la capture suivante de l'image disque :

![Le logiciel s'installe simplement dans le dossier Applications en faisant glisser son icône sur l'alias du dossier Applications.](http://zestedesavoir.com/media/galleries/2109/a1dd68b6-72e6-455f-ab7f-ac3a25e44eae.png.960x960_q85.png)

# Exécuter le code

Pour lancer le code écrit, il convient de l'enregistrer avec l'extension .rb. On peut ensuite le lancer dans l'application Terminal[^appterm] en y tapant `ruby␣` (le ␣ symbolise un caractère espace) suivi du chemin du fichier (ou en faisant glisser le fichier à la suite de la position du curseur dans le Terminal). Mais, même si certains s'en accommodent, c'est un peu lourd et les développeurs sont connus pour être paresseux. Pourquoi ne pas automatiser cela ?

## Automatisation de l'exécution du code par un script

L'application TextWrangler dispose d'une commande intégrée. Avec le code Ruby affiché devant vous, il vous suffit d'aller dans le menu **#!** (menu shebang) et d'y sélectionner « Run in Terminal » (les autres options d'exécution ne permettent pas de lancer un code demandant une saisie de l'utilisateur, vous ne pourrez pas entrer de donnée au clavier lors de l'exécution).

![On prend comme exemple le code situé [ici](https://zestedesavoir.com/tutoriels/373/une-introduction-a-ruby/497/les-bases/2489/les-conditions-et-les-boucles/#2-if-else)](http://zestedesavoir.com/media/galleries/2109/fc6ccf91-ff78-4a47-8845-11eaee2d37ec.png.960x960_q85.png)
Figure : On prend comme exemple le code situé [ici](https://zestedesavoir.com/tutoriels/373/une-introduction-a-ruby/497/les-bases/2489/les-conditions-et-les-boucles/#2-if-else)

![Le menu « shebang » dans la barre des menus](http://zestedesavoir.com/media/galleries/2109/8d823719-b924-4711-90bb-a2afa2226360.png.960x960_q85.png)
Figure : Le menu « shebang » dans la barre des menus


![L'article de menu « Run in Terminal »](http://zestedesavoir.com/media/galleries/2109/69d277b1-dcdb-4803-8a2e-c1dd5e2187db.png.960x960_q85.png)
Figure : L'article de menu « Run in Terminal »

![Lancement du code Ruby dans le Terminal. Il est demandé de saisir un âge.](http://zestedesavoir.com/media/galleries/2109/712198b5-aedc-402c-86e9-e819ded07839.png.960x960_q85.png)
Figure : Lancement du code Ruby dans le Terminal. Il est demandé de saisir un âge.

![Quand le code est fini d'être exécuté, on ne peut rien faire de plus dans la fenêtre ouverte.](http://zestedesavoir.com/media/galleries/2109/ddc584ec-3571-4c31-8f1b-1de723167d6c.png.960x960_q85.png)
Figure : Quand le code est fini d'être exécuté, on ne peut rien faire de plus dans la fenêtre ouverte.

Mais cette méthode intégrée ouvre une nouvelle fenêtre de Terminal par exécution de code. C'est pourquoi nous préconisons une autre méthode.

Nous allons configurer le logiciel afin d'avoir quelque chose de plus plaisant. Dans TextWrangler, créez un nouveau document et copiez-y scrupuleusement ce code (attention, la seconde ligne est très longue, allez jusqu'au bout) :

````bash
#!/bin/bash
osascript -e 'on run argv' -e 'tell application "Terminal"' -e 'activate'  -e 'delay 0.5' -e 'if ((count of (windows where visible is true)) = 0) then do script ""' -e 'do script "ruby "& (item 1 of argv) in window 1' -e 'end tell' -e 'end run' $BB_DOC_PATH > /dev/null 2>&1
````

[[information]]
| Des explications sur le code sont disponible à la fin de cette section.



Enregistrez ce document sous le nom `ruby.sh`. 

![Le code bash qui permet de lancer un code Ruby dans le Terminal](http://zestedesavoir.com/media/galleries/2109/c5ffea0a-9de1-42ac-9ea7-9fdf2fa3fd9f.png.960x960_q85.png)
Figure : Le code bash qui permet de lancer un code Ruby dans le Terminal

Allez dans le Finder. Choisissez le menu **Aller** avec la touche ||alt|| enfoncée. Ceci vous permettra d'accéder au dossier Bibliothèque (par défaut caché) de votre compte utilisateur. 

![Le dossier Bibliothèque ne s'affiche qu'en conjonction avec la touche « alt », pour éviter que des utilisateurs inexpérimentés y effacent des fichiers importants.](http://zestedesavoir.com/media/galleries/2109/815a9d45-7aad-4d8a-b81a-e2fe555c867f.png.960x960_q85.png)
Figure : [Le dossier Bibliothèque ne s'affiche qu'en conjonction avec la touche « alt », pour éviter que des utilisateurs inexpérimentés y effacent des fichiers importants.

Naviguez dans `/Application Support/TextWrangler/Scripts` et placez-y le fichier `ruby.sh` que vous venez de créer.

![Emplacement où il convient de placer « ruby.sh » afin qu'il soit accessible à partir de TextWrangler](http://zestedesavoir.com/media/galleries/2109/029ab514-8fd5-44c8-807c-c919ffd97906.png.960x960_q85.png)
Figure : Emplacement où il convient de placer « ruby.sh » afin qu'il soit accessible à partir de TextWrangler

Désormais, lorsque vous voudrez exécuter votre code Ruby, il vous suffira de vous rendre dans le menu **Scripts** (symbolisé par une feuille enroulée en forme de S, tel un parchemin :

![](http://zestedesavoir.com/media/galleries/2109/7832782a-f950-4590-b8ea-4b21618f0d75.png.960x960_q85.png)) 

de la barre de menus, et d'y choisir « ruby ». Cela placera l'application Terminal au premier plan et vous pourrez y voir votre code Ruby s'exécuter.

![Le menu Script dans la barre des menus.](http://zestedesavoir.com/media/galleries/2109/c0936d97-81bb-48f4-aa1c-22b5ef28fb23.png.960x960_q85.png)
Figure : Le menu Script dans la barre des menus.

![On sélectionne l'article « ruby » pour lancer le code Ruby dans le Terminal.](http://zestedesavoir.com/media/galleries/2109/89937995-3396-4628-b304-a67f3d47f1d2.png.960x960_q85.png)
Figure : On sélectionne l'article « ruby » pour lancer le code Ruby dans le Terminal.

[[information]]
| La fenêtre *Preferences* de TextWrangler permet, dans sa section « Menus & Shortcuts » de spécifier un raccourci clavier pour l'appel du script « ruby.sh » (cliquez sur la ligne « Scripts » puis double-cliquez sur le mot « none » grisé en face de « ruby » pour placer un raccourci clavier non utilisé dans d'autres articles de menus).

Les explications du code suivent :

[[secret]]
| Nous exécutons un script bash qui appelle un script AppleScript, exécuté avec la commande `osascript` (OSA : Open 
| Scripting Architecture[^OSA]). AppleScript est un langage à la syntaxe proche de l'anglais parlé. On peut y ajouter des 
| mot-clés sans signification comme « the » pour rendre le langage encore plus naturel : 
| **tell the application "TextWrangler"**. 
| 
| La commande `osascript` demande à ce que chaque ligne individuelle d'un script AppleScript soit séparée par une option 
| `-e` dont l'argument est la ligne de code AppleScript. Pour simplifier la compréhension, nous présentons le code 
| AppleScript sous sa forme standard :
| 
| ```applescript
| on run argv
|   tell application "Terminal"
|     activate
|     delay 0.5
|     if ((count of (windows where visible is true)) = 0) then do script ""
|     do script "ruby "& (item 1 of argv) in window 1
|   end tell
| end run
| ```
|
| La commande `osascript` peut recevoir des arguments à la fin de sa liste d'options. Ceci nous permet de fournir au code 
| AppleScript le chemin d'accès au fichier Ruby à exécuter. En effet, le logiciel TextWrangler fourni une variable 
| d'environnement `BB_DOC_PATH` dont la valeur est `$BB_DOC_PATH` (BB correspondant à Bare Bones, le développeur du 
| logiciel) qui permet à un script shell d'avoir le chemin d'accès au document ouvert au premier plan. Le code AppleScript 
| reçoit les arguments sous forme d'une liste ordonnée, et celle-ci est accessible par la variable `argv` du code. Le code 
| fait appel à l'application Terminal (ce qui provoque son ouverture le cas échéant). Si l'application était déjà ouverte, 
| mais en arrière-plan, `activate` la place au premier plan. On place le script en pause durant 0,5 seconde. Si on ne le 
| faisait pas, la ligne suivante, qui compte le nombre de fenêtres visibles -- certaines applications ont des fenêtres qui 
| peuvent être invisibles à un moment donné, comme des fenêtres de préférences -- de l'application Terminal serait faussée 
| dans le cas où l'application vient d'être ouverte : il y a un petit laps de temps entre l'ouverture de l'application et 
| l'affichage de sa fenêtre. Par sécurité, on met un délai de 0,5 seconde probablement largement supérieur à la valeur 
| nécessaire. S'il n'y a aucune fenêtre visible ouverte, on en crée une (normalement, le code serait « make new window », 
| mais un bug de longue date empêche son utilisation dans l'application Terminal. La solution de contournement est de 
| demander l'exécution d'un script shell vide sans préciser dans quelle fenêtre ça sera exécuté, de sorte que ça le fasse 
| dans une nouvelle fenêtre). Ceci est important, car la suite du code demande l'exécution du code Ruby dans la fenêtre au 
| premier plan. L'absence de fenêtre au premier plan provoquerait une erreur. Enfin, on lance le script Ruby en fournissant 
| son chemin d'accès, contenu dans la variable `argv` constitué d'une liste qui ici ne contient qu'un seul élément (donc on 
| en extrait la valeur avec `item 1 of argv`). Enfin, on termine le code par un petit raffinement, en redirigeant les 
| messages de sortie et d'erreur de la commande `osascript` vers nulle part, via `> /dev/null 2>&1`. Si on ne le faisait
| pas, TextWrangler intercepterait ces messages et les afficherait dans une fenêtre telle que celle-ci :
| 
| ![La fenêtre de journalisation (log) des messages des scripts shell tels que « ruby.sh ».](http://zestedesavoir.com/media/galleries/2109/9f1561ad-419d-4f17-a941-217da8aee7ac.png.960x960_q85.png)
| Figure : La fenêtre de journalisation (log) des messages des scripts shell tels que « ruby.sh ». 
|
| Toutefois les éventuelles erreurs survenant lors de l'exécution du code Ruby n'apparaitront pas dans ce fichier de log, 
| mais directement dans la fenêtre du Terminal. C'est pourquoi nous avons considéré que son affichage était inutile.

[^appterm]: L'application se trouve dans le dossier `/Applications/Utilitaires` d'OS X.

[^OSA]: https://developer.apple.com/library/mac/documentation/AppleScript/Conceptual/AppleScriptX/Concepts/osa.html
