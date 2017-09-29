# Plugin Mautic - INES CRM

Ce plugin permet de pousser des contacts de Mautic vers INES CRM avec l'action
_Envoyer le contact vers l'intégration_ ou la commande
`mautic:integration:fetchleads`.

Si vous n'avez pas encore de compte INES CRM,
[inscrivez-vous ici](http://www.inescrm.fr/).


## Configuration du plugin

1. Rendez-vous dans le menu plugins depuis la sidebar droite. Si vous ne voyez
pas l'icone INES CRM, cliquez sur le bouton
_Installer / Mettre à Jour les Plugins_.

2. Cliquez sur l'icone INES CRM et renseignez vos information de login,
assurez-vous de _Publier_ le plugin et de _Sauvegarder et Fermer_.

3. Cliquez sur l'icone INES CRM à nouveau. Si vous voyez un message d'erreur,
assurez-vous d'avoir renseigner les bonnes informations de login. Rendez-vous
dans l'onglet fonctionnalités et activez la synchronisation des Contacts et des
Sociétés puis cliquez sur _Sauvegarder et Fermer_.

4. Cliquez sur l'icone INES CRM une nouvelle fois. Liez vos champs de contacts
et de sociétés dans leurs onglets respectifs. Vous avez la possibilité de
configurer si la valeur envoyée par Mautic remplacera ou pas une valeur
existante dans INES CRM.

## Fonctionnalités

- Utilisez la fonctionnalité _Envoyer le contact vers l'intégration_ dans les
formulaires, les campagnes et les actions de points pour pousser des contacts à
INES CRM. À noter qu'un contact à besoin d'une adresse email et d'une société
pour être poussé vers INES.

- Ajouter la commande suivante à votre crontab pour régulièrement pousser les
nouveaux contacts.

  `app/console mautic:integration:fetchleads --integration=InesCRM --time-interval=[TIME-INTERVAL]`


## Tester le plugin

Suivez [ces instructions](./../plugins/integration_test.html).

## Crédit

Ce plugin a été dévelopé par [@webmecanik](https://github.com/webmecanik)
