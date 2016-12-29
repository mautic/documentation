# Plugin Mautic - iContact

Mautic peut envoyer les contacts vers [iContact](https://www.icontact.com) quand un contact fait une ou plusieurs actions.

## Autorisation

Pour connecter votre compte iContact avec votre instance Mautic, vous devez vous créer un compte sur iContact.
Suivez le [tutoriel](https://www.icontact.com/developerportal/documentation/register-your-app/) pour vous créer votre app.

Une fois votre app créée, vous devriez être capabale de voir cet écran :

![iContact - create a App Key](/plugins/media/plugins-icontact-authorization-details.png "iContact - create a App Key")

Renseignez les clés d'authentification Mautic - iContact :

- App ID = l'ID de application que vous avez créé
- App username = le login / email dont vous vous servez pour vous connecter à votre compte iContact (pas le nom de l'App).
- App password = Le mot de passe choisi pour approuver l'App.

![iContact - authorization](/plugins/media/plugins-icontact-authorization.png "iContact - authoriztion")

## Configuration du plugin

Allez sur l'onglet *Fonctionnalités* dans le plugin iContact dans Mautic. Selectionnez le segment iContact où les contacts de Mautic doivent être envoyés. Vous devriez y trouver un segment par défaut.

Les autres options de configuration sont :
- **Envoyer les contacts dans cette intégration** - qui est activée par défaut.

## Testez le plugin

Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.
