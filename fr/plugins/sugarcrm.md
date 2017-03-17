# Plugin Mautic - SugarCRM
La version bi-directionnelle du plugin a été ajoutée en 2.8.0, ce plugin peut pousser les contacts et les sociétés dans SugarCRM quand un contact fait une action (SugarCRM 6 Community & 7.x) ou s'il est simplement créé ou modifié (SugarCRM 6 Community). Le plugin permet également de récupérer les contacts, prospects et sociétés depuis SugarCRM (SugarCRM 6 Community). Si vous n'avez pas de compte SugarCRM, [créez-en un](https://www.sugarcrm.com/).

## Pré-requis
SSL. Votre instance Mautic doit être en HTTPS. SugarCRM n'acceptera pas la synchronisation sur un site en HTTP.

## Récupérez les identifiants API SugarCRM
Pour valider l'activation du plugin SugarCRM, vous devez vous munir d'accès API (Oauth keys) de votre compte SugarCRM (clés publiques et privées) ainsi qu'un identifiant et un mot de passe valides.

## Configuration du plugin SugarCRM de Mautic
1. Insérez les clés dans le plugin SugarCRM de Mautic.
2. Configurez les fonctionnalités que vous souhaitez activer.
3. Configurez le [mapping des champs](./../plugins/field_mapping.html) pour les contacts.
4. Configurez le [mapping des champs](./../plugins/field_mapping.html) pour les sociétés.
5. Sauvegarder et fermer le panneau de configuration du plugin.

### Fonctionnalités
Les fonctionnalités disponibles :
* Envoyer les contacts dans l'intégration à chaque fois qu'un contact est créé ou modifié en cochant la case “envoyer les contacts dans l'intégration”.
* Envoyer les contacts dans l'intégration seulement lorsqu'un contact fait une action de formulaire, campagne et déclencheurs de points en décochant la case “envoyer les contacts dans l'intégration”.
* Importer les données issues de l'intégration.
* Choisir quelles sont les données à importer de l'intégration entre les "Leads", "Contacts" et "Companies" de SugarCRM.
* Synchroniser le propriétaire du contact entre les deux applications SugarCRM et Mautic.
* Choisir quels sont les champs de Contacts/Leads/Companies vous souhaitez synchroniser avec le mapping.
* Mettre en place des règles de priorité sur les champs lorsqu'une valeur est déjà existante dans l'application cible.

### Commandes à activer pour l'échange des données (CRONs)
Pour les utilisateurs de Mautic en version Open source, vous devez ajouter ces lignes de commande pour mettre en place la synchronisation :
* `php app/console mautic:integration:fetchleads`
Pour pousser les activités des contacts synchronisés depuis Mautic vers le CRM, utilisez :
* `php app/console mautic:integration:pushleadactivity`

Les paramètres des commandes sont :
* **--time-interval** Pour paramétrer l'age des données à récupérer. Valeurs possibles : "10 days", "1 day", "10 minutes", "1 minute".  avec un maximum de "29 days". La valeur par défaut est 15 minutes.
* **--integration=SugarCRM** pour utiliser l'intégration SugarCRM.
Paramètre spécial pour `php app/console mautic:integration:fetchleads`
* **--fetch-all** Pour synchroniser tous les contacts depuis l'intégration. De préférence à n'utiliser que la première fois après l'installation.

Ces commandes peuvent être utilisées pour d'autres intégrations.

## Pour tester le plugin
Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.

## Crédits
Cette fonctionnalité a été développée par [@Webmecanik](https://github.com/webmecanik) et [@canal-web](https://github.com/canal-web).
