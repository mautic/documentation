# Plugin Mautic - Hubspot CRM

Ce plugin permet de pousser les contacts vers Hubspot CRM quand un contact fait une ou plusieurs actions. Si vous ne voyez pas ce plugin dans votre instance Mautic, Vérifiez que vous avez une version plus récente que la 1.2.3.

Si vous n'avez pas de compte Hubspot CRM, [créez en un ici](http://www.hubspot.com/crm).

## Clé API Hubspot

Visitez [https://app.hubspot.com/hapikeys](https://app.hubspot.com/hapikeys) pour générer votre clé API Hubspot.

## Configurez le plugin Hubspot CRM

1. Ouvrez le plugin Hubspot et collez la clé API dans le champ *clé API Hubspot*. De plus si vous souhaitez utiliser le plugin, vous devez l'activer. Paramétrez *Publier* à *Oui*.
2. Dans l'onglet Fonctionnalités, vous trouverez la case à cocher *Envoyer le contact dans l'intégration* qui est activée par défaut.
3. Configurez le [mapping des champs](./../plugins/field_mapping.html).
4. Sauvegardez la configuration du plugin.

![Hubspot CRM Plugin configuration](/plugins/media/plugins-hubspot-crm-configuration.png "Hubspot CRM Plugin configuration")

## Testez le plugin

Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.

## Troubleshooting

Si le contact n'a pas été créé, assurez vous d'avoir testé avec une adresse email valide. Hubspot ne créera un nouveau contact que lorsque l'adresse email est valide.

## Crédit

Ce plugin a été développé par [@gpassarelli](https://github.com/gpassarelli).
