# Plugin Mautic - Connectwise CRM

Ce plugin permet de récupérer et envoyer les contacts vers ou depuis Connectwise Manage.

## Pré-requis

- Un compte Connectwise
- Un ID d'entreprise issu de Connectwise
- Un rôle admin sur l'API Connectwise

## Obtenir les authentifiants Connectwise

Vous aurez besoin de votre ID d'entreprise pour pouvoir vous authentifier lors de la configuration du plugin Connectwise.
Pour créer un nouvel accès API vous devrez utiliser le client lourd. vous pouvez le télécharger [ici](https://university.connectwise.com/university/pageview.aspx?short_name=workstation-installation). Allez dans : *System/member* et créez un nouveau membre API ici. Vous aurez également un lien pour obtenir vos clés publiques et privées. Copiez ces informations.

## Configurez le plugin Mautic Connectwise

Insérez les clés dans le plugin Mautic Connectwise et lancez l'autorisation.
![Connectwise CRM Authorize](./../plugins/media/connectwiseauth.png "Connectwise CRM Authorize")

Configurez la [correspondance des champs](./../plugins/field_mapping.html).
Ajoutez une correspondance pour tous les champs en rouge, ce sont des champs obligatoires.

### Fonctionnalités

- Vous pouvez récupérer les contacts depuis l'intégration
- L'envoi des contacts se fait depuis les actions de campagne, de formulaire et de déclencheur de points.
- Sélectionnez les objets que vous souhaitez synchroniser.

La récupération des contacts se fait avec une ligne de commande à ajouter au CRON job.

### La ligne de commande pour récupérer les informations depuis Connectwise

- `php app/console mautic:integration:fetchleads`

Les paramètres suivants sont supportés sur la commande :

**--time-interval** Ce paramètre sert à choisir la plage de récupération des données. Supporte : "10 days", "1 day", "10 minutes", "1 minute".  Maximun de "29 days".

**--integration**=Connectwise pour utiliser l'intégration Connectwise.

## Tester le plugin

Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.
