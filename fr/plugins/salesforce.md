# Mautic - Salesforce CRM plugin

Ce plugin peut pousser les contacts présents dans Mautic vers Salesforce CRM lorsqu'ils réalisent des actions choisies. Si vous n'avez pas de compte Salesforce CRM, [créez en un ici](http://www.salesforce.com/).

## Pré-requis

SSL. Votre instance Mautic doit être en https. Autrement, Salesforce n'autorisera pas la synchronisation des données su un callback en http.

## Obtenir l'authorisation de connexion Salesforce

Il y a une [documentation officielle] (http://feedback.uservoice.com/knowledgebase/articles/235661-get-your-key-and-secret-from-salesforce) expliquant comment obtenir les clés de sécurité et d'identification, en revanche, elle ne semble pas vraiment à jour.
1. Allez dans **Setup** (en haut à droite) > Build (en bas à gauche) - Create > Apps > Connected Apps > New ![Salesforce CRM Create an App](/plugins/media/plugins-salesforce-create-app.png "Salesforce CRM Create an App")
2. Créez une nouvelle application de la manière suivante : ![Salesforce CRM Create an App form](/plugins/media/plugins-salesforce-create-app-form.png "Salesforce CRM Create an App form")
3. Soyez sûrs que l'authorisation sélectionnée (OAuth Scopes) sont *Access and manage your data* (api) et *Perform requests on your behalf at any time (refresh_token, offline_access)*.
4. Copiez la clé "Consumer Key" et la clé secrète. ![Salesforce CRM Create an App keys](/plugins/media/plugins-salesforce-create-app-keys.png "Salesforce CRM Create an App keys")

## Configurez le plugin Salesforce dans Mautic

Insérez les clés obtenues dans le plugin Salesforce dans votre compte Mautic et obtenez l'authorisation.
![Salesforce CRM Authorize](/plugins/media/plugins-salesforce-authorize.png "Salesforce CRM Authorize")

Configurez le [mapping des champs](./../plugins/field_mapping.html).

### Fonctionnalités
* Cela vous donne la possibilité de récupérer les contacts existants dans votre compte Salesforce ainsi qu'envoyer les contacts depuis votre compte Mautic vers votre compte Salesforce.
* L'envoi de contact se fait depuis une action (de campagne, formulaire ou un déclancheur de points).
* La récupération de contact se fait à la connexion et ensuite grace à des taches planifiées CRON (pour les utilisateurs de Mautic Open Source).
* Sélectionnez les objets que vous souhaitez pousser ou récupérer. Vous pouvez pousser vos contacts vers l'objet Leads dans Salesforce. vous pouvez également pousser des activités (fil d'activités du contact) dans un objet personnalisé dans Salesforce.
* La récupération d'informations sera faite depuis l'object Salesforce Leads et/ou Contacts.

### Lignes de commande pour récupére les contacts depuis Salesforce
Pour récupérer les contacts depuis Salesforce vous devez mettre en place une commande depuis CLI (pour les utilisateurs de Mautic Open Source). Paramétrez la commande suivante :

Utilisé pour récupérer les contacts depuis l'objet **Leads** dans Salesforce

`php app/console mautic:integration:fetchleads`

Utilisé pour poussez les activités dans un objet personnalisé Salesforce
`mautic:integration:pushleadactivity`

Chaque commande peut prendre en charge les paramètres :

* **--time-interval** qui permet de paramétrer le délai entre chaque récupération de données. Vous pouvez paraméter avec les valeurs : "10 days", "1 day", "10 minutes", "1 minute". Avec un maximum de délai de "29 days".
* **--integration=Salesforce**

## Paramétrer des objets personnalisés de Mautic dans Salesforce

Pour être capable de pousser des activités dans l'intégration Salesforce, il vous faut d'abord personnaliser un objet personnalisé dans votre compte Salesforce. Suivez les instructions ci après.

Nom de l'objet personnalisé : Mautic__timeline (nom API : Mautic_timeline__c)

nom des champs API :
* ActivityDate__c : Date\/Time
* contact_id__c : Lookup(Contact)
* Description__c : Long Text Area(131072)
* WhoId__c : Lookup(Lead)
* MauticLead__c : Number(18, 0) (External ID)
* Mautic_url__c : URL(255)

## Pour tester le plugin

Suivre [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.

## Troubleshooting

### Problématiques et erreurs

`Erreur : The REST API is not enabled for this Organization.``

Cela signifie que l'API n'est pas activée dans votre compte Salesforce, [voir plus](https://help.salesforce.com/apex/HTViewHelpDoc?id=admin_userperms.htm&language=en)
