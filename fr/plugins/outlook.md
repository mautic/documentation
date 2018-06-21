# Plugin Mautic - Outlook

Ce plugin permet pour l'Add-on Outlook de tracer les emails envoyés aux contacts depuis Outlook. Si vous ne le voyez pas, cliquez sur Installer/Mettre à jour les Plugins.

### Pré-requis

- Mautic installé sur une URL publique et accessible.
- Microsoft Outlook 2013 ou 2016.
- [Mautic Outlook Add-In pour Outlook 2013/2016](https://m.mautic.com/asset/24:microsoft-outlook-plugin-102)

### Configurez le plugin

Même si ce plugin est compatible avec Outlook 2013, vous trouverez ci après la description de l'installation pour la version compatible la plus récente, à savoir 2016.

1. Installez le plugin Mautic.
![image](/plugins/media/outlook/outlook_plugin.png)

2. Cliquez sur le bouton du plugin Outlook et entrez une clé secrète pour valider l'Add-In Outlook.
![image](/plugins/media/outlook/secret.png)

3. Lancez l'[Add-In Mautic Outlook](https://github.com/mautic/mautic/files/402928/Mautic.Outlook.Plugin.Setup.zip) sur une machine Windows avec Outlook 2016.

4. Dans la fenêtre d'options Outlook 2016, sélectionnez les Add-Ins et cliquez sur le bouton des options.
![image](/plugins/media/outlook/outlook_addin.png)

5. Renseignez l'URL de votre instance Mautic, avec la même clé secrète utilisée dans le plugon Mautic. Puis cliquez sur OK.
![image](/plugins/media/outlook/outlook_settings.png)

6. Pour tracer un email envoyé à un contact, cliquez sur le bouton **Track Email** dans la fenêtre de nouvel email.
![image](/plugins/media/outlook/outlook_send.png)

7. Cela ajoutera un pixel de tracking GIF à votre email avec la forme suivante :  [[MAUTIC_URL]]/index.php/outlook/tracking.gif?d=H4sIAAAAAAAEAIVRTW%2FCMAz9LRyCtgNVlFBpHHroWsRuk8ak7RpaUzqaGCUp0H8%2Fpy0TH4dJUZy892w921uLOvkCa8BGK2WLWi2dt6pUbM7PYPEcFainoFXdJKdBVvUy4quA9rxrNz9Q%2BCQ16HdgmeAenKewpfIU3lvfIO6nGyy75HNXO8LQAN3984R2X5tqMpkwnjOejrfg19%2FBJIHBJsskS3M1MOvOedChUA5HaPBAsp54a7UyBH%2BAw9YWECRrsMc6PHvFd2iR0NfW1QbcjUDwMjhctYqqq0YxkQU6SqMhNxi85GeoD8p0134zaBom%2By4ezlPMxTPFeCH5TLzI%2BdgizeEu5aIUQixmIubjSG5WAY8bC8kyC%2FvxSBX%2Flcvl3bT%2Fvr8k1oBgIQIAAA%3D%3D&sig=cf078d5b

8. Le plugin Mautic validera l'information en comparant les clés secrètes et ajoutera ensuite l'événement à l'historique du contact dans Mautic. Si le(s) contact(s) n'existe pas déjà, il sera créé automatiquement.
![image](/plugins/media/outlook/outlook_contacts.png)

![image](/plugins/media/outlook/outlook_timeline.png)

## Problèmes de longueur de paramètre URL
Veuillez noter que les paramètres PHP avec le patch suhosin installé aura comme valeur par défaut une limite de 512 caractères pour les paramères GET. Cependant, la majorité des navigateurs (incluant IE) supportent les URLs jusqu'à 2000 caractères alors qu'Apache à une valeur par défaut de 8000.
Pour supporter des paramètres plus longs, ajouter le paramètre suivant dans php.ini
`suhosin.get.max_value_length = 5000`
