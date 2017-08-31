# Plugin Mautic - vTiger CRM

Mautic peut envoyer les contacts vers vTiger CRM quand un contact fait une ou plusieurs actions.

Si vous n'avez pas encore de compte vTiger CRM, [créez le ici](https://www.vtiger.com/).

## Authentification du plugin vTiger

Pour authentifier le plugin Mautic pour qu'il communique avec vTiger CRM vous avez besoin de paramétrer cela :

- **vTiger URL** - l'URL commencant par http:// ou https:// où votre compte vTiger fonctionne (ex. `https://your_vtiger.od2.vtiger.com`).
- **vTiger username** - Votre login (adresse email généralement) qu vous utilisez pour vous connecter à votre compte vTiger.
- **vTiger access key** - La clé d'accès publiée dans votre profil vTiger. Pour l'obtenir, allez dans *My Preferences* dans vTiger. Le hash de la *clé d'accès* est en bas de la page.

Renseigenz ces 3 informations dans le plugin Mautic et authentifiez vous.

## Configurez le plugin vTiger CRM

1. Si vous souhaitez utiliser le plugin, vous devez l'activer. Paramétrez *Publier* à *Oui*.
2. Dans l'onglet Fonctionnalités, vous trouverez la case à cocher *Envoyer le contact dans l'intégration* qui est activée par défaut.
3. Configurez le [mapping des champs](./../plugins/field_mapping.html).
4. Sauvegardez la configuration du plugin.

## Testez le plugin

Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.
