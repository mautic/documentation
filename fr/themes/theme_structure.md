# Structure des thèmes

## Architecture des dossiers

Un thème doit se situer dans un dossier propre qui porte son nom (un par thème). Le fichier doit être envoyé dans votre instance Mautic via transfert FTP ou par import [depuis l'interface](theme_structure.md) (depuis Mautic 2.2.0).

![Theme folder structure](/themes/media/themes-folderstructure.png "Theme Folder Structure")

## Structure des fichiers

Les thèmes Mautic ont généralement une structure similaire, comme vous pouvez le constater sur les thèmes pré-existants sur votre instance Mautic.

![Theme file structure](/themes/media/themes-filestructure.png "Theme File Structure")

Dans le dossier du thème, il y a un sous dossier qui contient les fichiers CSS, les fichiers PHP, et parfois des images.  Il y également le fichier config.php qui contient les paramétrages basiques du thème.

### Config.php

La configuration du fichier contient un tableau qui spécifie le nom du thème, les fonctionnalités concernées (ex. page d'atterrissage, email, formulaire, etc.) et les zones éditables dans les différents thèmes.

### CSS
Dans le dossier CSS, vous y placerez les feuilles de style requises dans les thèmes, gardez le nom du fichier en correspondance avec le nom du thème pour plus de commodités.

Le style utilisé dans les thèmes peut être ajusté et modifié, en revanche, nous vous recommandons de changer le nom du thème à chaque version (après clone) pour une meilleure gestion des problématiques de cache.

### HTML
Le dossier HTML contient les fichiers de structure des thèmes.

Vous pouvez y retrouver les fichiers suivants :

* base.html.php
* email.html.php
* form.html.php
* message.html.php
* page.html.php

#### base.html.php
Ce fichier contient la structure de base pour les pages d'atterrissage, incluant les balises <head></head>, et la gestion des fichiers de styles et javascript liés.

#### email.html.php
Ce fichier contient la structure et le style inline qui sera généré dans votre éditeur d'email utilisant ce style.

#### form.html.php
Ce fichier contient la structure et la forme des formulaires qui sont associés au thème.

#### message.html.php
Ce fichier sert à afficher les messages d'alerte - comme les messages d'après soumission de formulaire.

#### page.html.php
Ce fichier contrôle la forme et la gestion des zones pour les pages d'atterrissage.

### Images
Si des images sont utilisées dans votre thème, elles peuvent être hébergées dans un dossier dans le thème. Ce fichier ne doit pas exister si vous n'utilisez pas d'images dans le thème.
