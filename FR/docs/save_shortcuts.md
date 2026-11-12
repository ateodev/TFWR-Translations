# Copies avec Raccourcis
L'app Raccourcis peut copier tes sauvegardes à l'endroit de ton choix, comme iCloud Drive, chaque fois que tu quittes le jeu. Elle le fait toute seule, sans rien demander. Cela fait partie du jeu complet.

## Mise en place
1. Dans **Raccourcis**, touche + pour créer un nouveau raccourci, touche **Modifier** en haut à droite et ajoute l'action du jeu **Obtenir la dernière sauvegarde**.
2. Ajoute **Enregistrer le fichier** et touche sa flèche. Désactive **Demander où enregistrer**, choisis un dossier et active **Écraser si un fichier existe**.
3. Touche **Rechercher** en bas, puis **Automatisation**, et sous **Apps** choisis **App**.
4. Dans la ligne qui apparaît, touche **App** et choisis le jeu, puis touche **Ouverte** et choisis **Fermée**.

Avant iOS 27, crée plutôt l'automatisation dans l'onglet **Automatisation** : choisis **App**, le jeu, seulement **Est fermée** et **Exécuter immédiatement**, puis ajoute-lui les actions des étapes 1 et 2. Sous iOS 16, désactive plutôt **Demander avant d’exécuter**.

Chaque copie est un zip qui porte le nom de sa sauvegarde, tu gardes donc une copie à jour de chaque sauvegarde.

## Garder les anciennes copies
Mets la variable **Date actuelle** dans le chemin du dossier de l'action **Enregistrer le fichier**. Les copies d'une autre date vont alors dans un dossier à part, et les anciennes restent.

## Autres actions
**Obtenir une sauvegarde** récupère une sauvegarde par son nom. **Obtenir les sauvegardes** récupère toutes les sauvegardes, ou seulement celles modifiées depuis une date.

## Récupérer une copie
Les actions ne font que copier tes sauvegardes vers l'extérieur. Pour récupérer une copie, appuie sur « Importer » sur l'écran de chargement et choisis son zip.

La sauvegarde cloud garde tes appareils au même stade de progression. Une copie de Raccourcis est ton propre fichier, rangé là où tu le choisis, pour l'historique ou pour le jeu sur PC.
