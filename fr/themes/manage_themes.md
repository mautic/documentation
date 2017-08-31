# Gestion des thèmes

## Gestionnaire de thème

Depuis la version de Mautic 2.1.0, le gestionnaire de thèmes a été ajouté et vous pouvez directement les gérer depuis l'interface dans le menu de configuration en haut à droite.

Le tableau des thèmes installés vous montre le nom des thèmes, les auteurs, le lien vers son site s'il est renseigné. Vous pouvez également le prévisualiser (si renseigné) pour voir un screenshot du thème.

### Installer un nouveau thème

Un nouveau thème peut être installé avec un zip. Le fichir zip doit avoir la même structure que les thèmes déjà pré-installés dans Mautic. Il vous faudra donc vous assurer d'avoir le fichier `config.json` à la racine du dossier de votre zip. Vous pouvez en trouver plus dans la [documentation développeur](https://developer.mautic.org/#theme-directory-structure).

Si votre thème est prêt en zip, vous pouvez le charger sur votre compt Mautic depuis le panneau de configuration. Cliquez sur le bouton "Choisir le fichier" pour sélectionner votre zip, puis cliquez sur Installer. Vous serez averti si l'installation a réussi ou échoué, le nouveau thème apparait dans le tableau des thèmes.

### Télécharger un thème existant

Si vous souhaitez créer votre propre thème, le plus simple est de télécharger un thème existant et de le modifier. L'option de téléchargement est disponible dans la liste déroulante à côté de chaque thème dans le tableau des thèmes.

### Mettre à jour un ancien thème

Les anciens fichier de thème sont écrasés par les nouveaux lorsque vous l'importer avec le même nom.
Les thèmes pré-installés ne peuvent pas être écrasés car ces modifications ne seraient pas sauvegardées après les mises à jour.

### Supprimer un thème

Aller dans le gestionnaire de thèmes, cochez le thème que vous souhaitez supprimer et puis cliquez sur le bouton rouge de suppression.

Les thèmes pré-installés ne peuvent pas être supprimés car ils reviendraient après chaque mise à jour de votre compte Mautic.

## Choisir un thème par défaut

Il est possible de choisi un thème par défaut sur votr instance Mautic en modifier la configuration générale. Pour procéder ainsi, vous devais avoir les droits vous permettant de le faire. Cliquez sur le bouton d'administration en haut à droite de votre écran, et cliquez sur 'Configuration'.

Depuis cet écran, les thèmes disponible sont affichés dans une liste déroulante qui peut être sélectionnée. En sauvegardant, vous appliquerez le thème choisi à tous les objets n'ayant pas de thème attribué.

![Configure themes under Administration Settings->System Settings](/themes/media/theme-config.jpg)

Les thèmes sont disponibles pour les emails et les pages d'atterrissage sur la page principale d'édition.

![Select a theme for a new page](/themes/media/themes2.jpg)
