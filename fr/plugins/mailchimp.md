# Plugin MailChimp

Mautic peut envoyer les contacts dans MailChimp avec l'action *Envoyer le contact dans l'intégration* que vous pouvez retrouver dans les campagnes, les formulaires et les délencheurs de points.

## Authorisation

### Obtenir la clé API MailChimp

1. Créez un compte MailChimp si vous n'en avez pas déjà un.
2. Allez dans *Account* / *Extras* / *API Keys* et créez une nouvelle clé API.
3. Copiez les informations de la clé créée.

![MailChimp - create a API Key](/plugins/media/plugins-mailchimp-create-api-key.png "MailChimp - create a API Key")
![MailChimp - copy the API Key](/plugins/media/plugins-mailchimp-copy-api-key.png "MailChimp - copy the API Key")

### Authorisation du plugin Mautic - MailChimp

Renseignez le **username** afin de vous connecter avec votre compte MailChimp ainsi que la **clé API**. Sauvegardez.

## Configurer le plugin

Allez dans l'onglet *Fonctionnalités* du plugin. Vous devriez voir ce message :

> The Contact Field Mapping tab will appear after selecting a segment and will update after changing the selected segment.

![MailChimp Plugin configuration](/plugins/media/plugins-mailchimp-configure.png "MailChimp Plugin configuration")

Sélectionnez alors un segment. Si vous n'avez pas de segment dans MailChimp, allez dans *MailChimp dashboard* / *Segments* / *Create List* et créez en un nouveau. Sauvegardez la configuration du plugin et ouvrez le à nouveau. L'onglet de *Mapping des champs du contact* devrait maintenant s'afficher. Configurez la [mapping des champs](./../plugins/field_mapping.html).

Les autres options de configuration sont :
- **Envoyer le contact vers l'intégration** - Cette option est activée par défaut. Si vous la désactivez, le plugin n'enverra plus les contacts vers MailChimp.
- **Activer double opt in** - Si MailChimp soit envoyer un email de confirmation lorsque le contact passe dans cette synchronisation. Le contact devra par cet email confirmet qu'il souhaite réellement rentrer dans le segment MailChimp.
- **Envoyer un email de bienvenue** - Si MailChimp doit envoyer un email de bienvenue au contact synchronisé.

## Tester le plugin

Voir les [étapes ici](./../plugins/integration_test.html) pour tester l'intégration.
