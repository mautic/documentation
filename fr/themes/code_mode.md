# Code Mode

Le **mode code** est une option disponible dans l'éditeur de page d'atterrissage et d'email. Cela vous permet de créer/insérer/modifier un contenu en code HTML. Cela peut être utile lorsque vous ne souhaitez pas utiliser l'éditeur Mautic ou les thèmes en collant du code issu d'un outil tierce ou si vous aimez vraiment beaucoup tout faire à la main !

Code Mode a été introduit en version de Mautic 2.3.0 en remplacant la page d'édition de Froala (WYSIWYG) qui interprétait légèrement le code HTML importé. Avec le mode code, le code importé n'est pas du tout modifié et enregistré tel quel.

## Sélectionner le Code Mode

Le Code Mode peut être sélectionné dans les thèmes lorsque vous créez un nouvel email. Une fois ce mode sélectionné, lancez le générateur d'email et vous pourrez tout faire de là.

### Limitations

Si vous utilisez un thème Mautic et que vous souhaitez modifier le code HTML dans le générateur Code Mode, vous pouvez le faire, mais vous ne pourrez plus plus revenir sur l'édition du thème par la suite. Vous serez condamné à continuer à l'éditeur en mode code. Si vous sélectionnez un thème, cela va écraser le contenu déjà existant.

![Sélectionner le Code Mode](/themes/media/code-mode-select.png)

## Modifiation du contenu HTML dans le générateur Code Mode

Une fois le générateur de code ouvert, vous verez la prévisualisation sur la gauche, et le code HTML sur la droite. La prévisualisation est mise à jour toutes les 10 secondes.

### Les tokens Mautic

Vous avez la possibilité d'utiliser les tokens dans le Code Mode en les écrivant directement. Par exemple, `{contactfield=firstname}`.

![Edit the HTML with Code Mode](/themes/media/code-mode-builder.png)

### Gestion des medias

Il y a un bouton en haut de la zone de code pour ouvrir le gestionnaire des medias pour importer et/ou sélectionner une image ou d'autres fichiers. Si vous sélectionnez un fichier, l'URL du fichier sera insérée à l'endroit où se trouvait le curseur.
