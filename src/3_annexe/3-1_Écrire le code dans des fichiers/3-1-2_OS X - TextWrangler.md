Sous OS X, vous disposez aussi de plusieurs éditeurs de texte. Un très bon éditeur est TextWrangler. Il s'agit tout comme Notepad++ d'un éditeur gratuit, mais il est sous licence propriétaire. TextWrangler est très utilisé, alors vous êtes sûr d'obtenir de l'aide si vous avez un problème.

TextWrangler est le petit frère gratuit de BBEdit. Ils sont tous deux édités par *Bare Bones* et si TextWrangler dispose de moins de fonctionnalités, il est largement suffisant pour nous. Vous pouvez voir les différences entre les deux logiciels [ici](http://www.barebones.com/products/bbedit/comparison.html) sur le site de l'éditeur (en anglais).

# Installer TextWrangler

Pour télécharger TextWrangler, vous pouvez tout simplement aller sur le Mac App Store, le rechercher et l'installer (lien direct de l'aperçu de l'application, permettant d'accéder sur la page correspondante du Mac App Store pour les habitants de France : [https://itunes.apple.com/fr/app/textwrangler/id404010395?mt=12](https://itunes.apple.com/fr/app/textwrangler/id404010395?mt=12)).

Néanmoins, les mesures de sécurité imposées par Apple au Mac App Store (voir l'article [Sandbox (sécurité informatique)](https://fr.wikipedia.org/wiki/Sandbox_(sécurité_informatique)) sur Wikipédia) ne permettent pas au logiciel d'accéder à des dossiers tels que `\etc`, n'appartenant pas à l'utilisateur courant. De même, le logiciel obtenu à partir du Mac App Store n'installe pas des outils supplémentaires en ligne de commande.

C'est pourquoi nous recommandons aux utilisateurs avancés de le télécharger directement sur le [site de l'éditeur](http://www.barebones.com/products/textwrangler/). Le lien est, au moment où nous écrivons, dans le menu à droite. Il suffit de cliquer sur le bouton ||Download Now|| pour obtenir la dernière version disponible. Vous obtiendrez un fichier `dmg`. En double-cliquant sur ce fichier, vous le monterez (en fait c'est une image disque) et vous pourrez exécuter le logiciel, après l'avoir installé sur le disque dur, de préférence dans le dossier Applications, ce qui est réalisé très simplement en faisant glisser l'icône de gauche sur l'icône de droite, comme indiqué dans la capture suivante de l'image disque :

![Le logiciel s'installe simplement dans le dossier Applications en faisant glisser son icône sur l'alias du dossier Applications.](http://zestedesavoir.com/media/galleries/2109/a1dd68b6-72e6-455f-ab7f-ac3a25e44eae.png.960x960_q85.png)

# Exécuter le code

Pour lancer le code écrit, il convient de l'enregistrer avec l'extension .rb. On peut ensuite le lancer dans l'application Terminal[^appterm] en y tapant `ruby␣` (le ␣ symbolise un caractère espace) suivi du chemin du fichier (ou en faisant glisser le fichier à la suite de la position du curseur dans le Terminal). Mais, même si certains s'en accomodent, c'est un peu lourd et les developeurs sont connus pour être paresseux. Pourquoi ne pas automatiser cela ?

## Automatisation de l'exécution du code par un script

L'application TextWrangler dispose d'une commande intégrée. Avec le code Ruby affiché devant vous, il vous suffit d'aller dans le menu **#!** (menu shebang) et d'y sélectionner « Run in Terminal » (les autres options d'exécution ne permettent pas de lancer un code demandant une saisie de l'utilisateur, vous ne pourrez pas entrer de donnée au clavier lors de l'exécution). Mais cette méthode intégrée ouvre une nouvelle fenêtre de Terminal par exécution de code. C'est pourquoi nous préconisons une autre méthode.

Nous allons configurer le logiciel afin d'avoir quelque chose de plus plaisant. Dans TextWrangler, créez un nouveau document et copiez-y scupuleusement ce code (attention, la seconde ligne est très longue, allez jusqu'au bout) :

````bash
#!/bin/bash
export BB_DOC_PATH;osascript -e 'on run argv' -e 'tell application "Terminal"' -e 'activate' -e 'if ((count of (windows where visible is true)) = 0) then do script ""' -e 'do script "ruby "& (item 1 of argv) in window 1' -e 'end tell' -e 'end run' $BB_DOC_PATH
````

(`BB_DOC_PATH` est une variable d'environnement du logiciel TextWrangler (BB correspondant à Barebones, l'éditeur) qui permet à un script shell d'avoir le chemin d'accès au document ouvert au premier plan)

Enregistrez ce document sous le nom `ruby.sh`. Allez dans le Finder. Choisissez le menu **Aller** avec la touche ||alt|| enfoncée. Ceci vous permettra d'accéder au dossier Bibliothèque (par défaut caché) de votre compte utilisateur. Naviguez dans `/Application Support/TextWrangler/Scripts` et placez-y le fichier `ruby.sh` que vous venez de créer.

Désormais, lorsque vous voudrez exécuter votre code Ruby, il vous suffira de vous rendre dans le menu **Scripts** (symbolisé par une feuille enroulée en forme de S, tel un parchemin) de la barre de menus, et d'y choisir « ruby ». Cela placera l'application Terminal au premier plan et vous pourrez y voir votre code Ruby s'exécuter.

Vous remarquerez que TextWrangler affiche une fenêtre de log (consigne dans un journal) les appels au fichier `ruby.sh`. Toutefois les éventuelles erreurs survenant lors de l'exécution du code Ruby n'apparaitront pas dans ce fichier de log, mais directement dans la fenêtre du Terminal. Si l'affichage de ce fichier de log est plus une contrainte qu'une utilité à vos yeux, vous pouvez utiliser une méthode alternative, détaillée dans la suite, par défaut masquée (le code AppleScript, qui est aussi employé dans le script shell précédent, sera expliqué).

[[secret]]
| Une alternative consiste à lancer un script AppleScript plutôt qu'un script shell. Ouvrez l'application « Éditeur de script »[^nomAS], créez un nouveau document (||cmd||+||N||) et placez-y ce code :
|
| ````applescript
| tell application "TextWrangler"
|	set fichier to file of window 1
| end tell
|
| tell application "Finder"
| 	set chemin to POSIX path of fichier
| end tell
|
| tell application "Terminal"
|	activate
|   if ((count of (windows where visible is true)) = 0) then do script ""
|	do script "ruby " & quoted form of chemin in window 1
| end tell
| ````
|
| Allez dans **Fichier**>**Enregistrer...** et gardez le format de fichier Script. Nommez le fichier `ruby-AS.scpt` par exemple. Placez ce fichier au même emplacement que le fichier `ruby.sh` vu précédemment. Désormais, dans TextWrangler, lorsque vous voudrez exécuter votre fichier Ruby, il vous suffira d'aller comme précédemment dans le menu **Script** mais cette fois d'y sélectionner « ruby-AS ». Vous n'aurez pas cette fois l'inconvénient de la fenêtre de log qui se rajoute dans TextWrangler.
|
| [[information]]
| | Voici quelques explications sur le code AppleScript proposé. Il s'agit d'un langage à la syntaxe proche de l'anglais parlé. On peut y ajouter des mot-clés sans signification comme « the » pour rendre le langage encore plus naturel : **tell the application "TextWrangler"**. Dans un premier temps, on place dans la variable `fichier` l'objet correspondant au fichier ruby au premier plan. Puis on place, via l'explorateur de fichier d'OS X **Finder.app**, le chemin Unix du fichier dans la variable `chemin`. Ensuite, on appelle l'application Terminal.app, on l'active afin de la placer au premier plan, et on comptabilise le nombre de fenêtres visibles déjà ouvertes (certaines applications ont des fenêtres qui peuvent être invisibles à un moment donné). S'il n'y a aucune fenêtre visible ouverte, on en crée une (normalement, le code serait « make new window », mais un bug de longue date empêche son utilisation dans l'application Terminal. La solution de contournement est de demander l'exécution d'un script shell vide sans préciser dans quelle fenêtre ça sera exécuté, de sorte que ça le fasse dans une nouvelle fenêtre). Ceci est important, car la suite du code demande l'exécution du code Ruby dans la fenêtre au premier plan. L'absence de fenêtre au premier plan provoquerait une erreur.
| |
| |  Dans le code du script de l'autre méthode, la variable `argv` reçoit les paramètres de la commande osascript (OSA : Open Scripting Architecture[^OSA]) sous forme de liste ordonnée. Ainsi, `argv` reçoit une liste d'un élément, `$BB_DOC_PATH`. Le premier (et seul) élément de cette liste sera donc : `item 1 of argv`.
 

[^appterm]: l'application se trouve dans le dossier `/Applications/Utilitaires` d'OS X.
[^nomAS]: l'application, dans les versions plus anciennes d'OS X, se nommait « Éditeur AppleScript », mais son interface est globalement la même, de sorte que vous ne serez pas dépaysé si vous ne disposez pas d'OS X Yosemite ou ultérieur. Elle se trouve dans le même dossier que l'application Terminal.
[^OSA]: https://developer.apple.com/library/mac/documentation/AppleScript/Conceptual/AppleScriptX/Concepts/osa.html
