# Gestion des thèmes

## Gestionnaire de thème

Depuis la version de Mautic 2.1.0, le gestionnaire de thèmes a été ajouté et vous pouvez directement les gérer depuis l'interface dans le menu de configuration en haut à droite.

Le tableau des thèmes installés vous montre le nom des thèmes, les auteurs, le lien vers son site s'il est renseigné. Vous pouvez également le prévisualiser (si renseigné) pour voir un screenshot du thème.

### Installer un nouveau thème

Un nouveau thème peut être installé avec un zip. Le fichir zip doit avoir la même structure que les thèmes déjà pré-installés dans Mautic. Il vous faudra donc vous assurer d'avoir le fichier `config.json` à la racine du dossier de votre zip. Vous pouvez en trouver plus dans la [documentation développeur](https://developer.mautic.org/#theme-directory-structure).

If you have the theme zip package either created by yourself or downloaded from a theme provider, in the top right corner of the Themes page is the upload form. Click the "Choose File" button to choose the zip file, then click Install. The notice will appear if the installation was successful and if so, the new theme appears in the table of currently installed themes.

### Download an existing theme

If you want to create your own theme, the simplest way to do that is to download and existing theme and modify it. The download option is in the drop down menu next to every theme in the Theme Manager table.

### Update an old theme

The old theme files will be overwritten by the new one when installing a theme which already exists in your Mautic. Therefore, the theme updates can be also done by the Theme Manager's Install form.

The pre-installed themes cannot be overwritten because the changes would return again after a Mautic update.

### Delete a theme

Go to the Theme Manager, check what theme(s) you want to delete and then click the red button above the theme table to delete them.

The pre-installed themes cannot be deleted because they would appear again after a Mautic update.

## Assigning a default theme

It is possible to assign a default theme to a Mautic instance by editing the global configuration.  To access the global configuration you must be logged in with sufficient access.  Click on the cog icon beside the logged in user, and select 'Configuration'.

From the configuration screen, the available themes will be listed in a dropdown box, which can be selected.  On saving, this setting will apply for all resources which do not have a theme explicitly specified.

![Configure themes under Administration Settings->System Settings](/themes/media/theme-config.jpg)

Themes are available for emails and landing pages on each one's main editing page

![Select a theme for a new page](/themes/media/themes2.jpg)
