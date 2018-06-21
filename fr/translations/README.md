# Traductions

Mautic est utilisé par une communauté planétaire et peut donc pas conséquence être utilisé dans n'importe quelle langue. Si vous ne trouvez pas votre langue, n'hésitez pas à contribuer en regardant la section "comment traduire Mautic".

## Comment sélectionner une langue dans Mautic

Cela peut être effectué à deux endroits.

### 1. Langue pas défaut

Dans la configuration Mautic, vous pouvez choisir une langue par défaut. Par défaut, c'est en `English - United States`. Chaque utilisateur aura la plateforme en cette langue s'il ne va pas modifier sa propre langue utilisateur. Pour modifier la langue par défaut :

1. Ouvrez le panneau d'administration en haut à droite de la fenêtre de votre navigateur.
2. Sélectionnez le menu *Configuration*.
3. Sélectionnez la langue par défaut de votre choix.
4. Sauvegardez.

![Select the default language](/translations/media/translations-select-language.png "Select the default language")

### 2. Langue de l'utilisateur

L'utilisateur peut définir sa propre langue qui prendra le dessus sur la langue par défaut de l'application. Cela permet à une équipe multilingue de collaborer au mieux. Pour procéder ainsi :

1. Ouvrez le menu utilisateur en haut à droite.
2. Cliquez sur *Account*.
3. Sélectionnez la langue de votre choix.
4. Sauvegardez.

![Select the user language](/translations/media/translations-select-user-language.png "Select the user language")

## Comment traduire Mautic

Mautic peut être traduit dans n'importe quelle langue. Comme Mautic est un projet communautaire, il peut ête traduit par n'import quel membre de la communauté. Les traductions s'effectuent depuis l'application [Transifex](https://www.transifex.com/mautic/mautic/).

1. Créez une compte sur [Transifex](https://www.transifex.com/mautic/mautic/) si vous n'en avez pas déjà un.
2. Consultez la [liste des langues](https://www.transifex.com/mautic/mautic/) déjà créées pour le projet.
3. Créez une langue si elle n'est pas déjà existante, ou contribuez à une langue existante.

Consultez la [documentation Transifex](http://docs.transifex.com/tutorials/txeditor/) si vous vous posez des questions sur le processus de traduction.

## Comment mettre à jour une langue

La langue est mise à jour à chaque fois que la configuration est sauvegardée ou si cette langue n'avais auparavant jamais été téléchargée. En revanche, Mautic ne téléchargera pas la langue si elle a déjà été téléchargée. Pour mettre à jour une langue, procédez ainsi :

1. Ouvrez les fichiers système Mautic via le SFTP ou le SSH.
2. Dans le dossier root de Mautic, vous devriez voir un fichier nommé *translations*. Ouvrez le.
3. Dans ce dossier *translations* vous touverez les langues stockées. Supprimez les dossiers des langues que vous souhaitez mettre à jour.
4. Rendez vous sur votre instance Mautic dans la configuration et sauvegardez avec la langue supprimée.

La langue devrait être téléchargée à nouveau avec les traductions les plus récentes. Les traductions sont générées par Transifex une fois par jour.

Si vous avez des questions à propos des traductions, rejoignez la communauté sur [Slack channel #Translations](https://www.mautic.org/slack/).
