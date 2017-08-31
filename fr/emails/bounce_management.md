# Monitoring des emails
Depuis la version 1.2.0 de Mautic, vous avez la possibilité de remonter les informations IMAP pour détécter les rebons (bounced) et les requêtes de désinscription (unsubscribe).

## Paramétrage des boites de réception monitorées
Pour utiliser les emails monitorés, vous devez avoir l'extension PHP IMAP activée (la majorité des hôtes l'ont activé par défaut).  Allez dans votre configuration Mautic remplissez les détails de votre compte à monitorer.

![Monitored inbox settings](/emails/media/asset-monitored-inbox-settings.png "Monitored inbox settings")

Pour récupérer et traiter les messages, lancez la commande suivante (pour les utilisateurs Mautic Open Source) :

```
php /path/to/mautic/app/console mautic:email:fetch
```

Notez qu'il est recommandé de créer une adresse spécifique pour cet usage puisque Mautic va lire chaque message présent dans ce dossier.

Si vous envoyez les emails par Gmail, le chemin de retour de l'email sera automatiquement reécrit avec l'adresse Gmail.

Si vous sélectionnez un dossier de désinscription, Mautic attachera également à cet email l'en-tête "List-Unsubscribe". Ainsi, cela ajoutera automatiquement le contact dans le dossier des désinscrits.

## Créez un segment avec les emails rebonds

Ce n'est pas obligatoire, mais si vous souhaitez avoir une vue sur vos contacts email en rebond, créez un segment comme suivant.

1. Allez dans *Segments* / *Nouveau*.
2. Nommez le segment. Par exemple *Bounced emails*.
3. Allez dans l'onglet *Filtres*.
4. Créez un nouveau filtre *Email Rebond* avec la valeur Oui.
5. Attendez la mise à jour du segment avec le CRON `app/console mautic:segments:update` pour la mise à jour du segment.

## Mandrill Webhook

Mautic supporte certaines webhooks de Mandrill pour les rebonds.  

1) Connectez vous à votre compte Mandrill puis allez dans "Settings" -> "Webhooks"

![Webhooks](/emails/media/mandrill_webhook_1.png "Mandrill webhooks")

2) Cliquez sur "Add Webhook"

![Add Webhook](/emails/media/mandrill_webhook_2.png "Add webhook")

3) Mautic 1.2.2 supporte les webhooks suivantes : Message is Bounced, Message is Soft-Bounced, Message is Rejected. Depuis la version 1.2.3, Message is Marked as Spam et Message Recipient Unsubscribes sont supportés.

4) Remplissez l'URL de rappel `http://your-mautic.com/mailer/mandrill/callback` et cliquez sur Create Webhook.

5) Cliquez sur Custom Metadata et créez deux nouveaux champs de metadata : `hashId` et `contactId`

![Add metadata](/emails/media/mandrill_webhook_5.png "Add metadata")

![Add metadata](/emails/media/mandrill_webhook_4.png "Add metadata")

## Sparkpost Webhook

1) Connectez vous à votre compte Sparkpost et allez dans "Account" -> "Webhooks".

![Webhooks](/emails/media/sparkpost_webhook_1.png "Sparkpost webhooks")

2) Cliquez sur le bouton "New Webhook" en haut à droite

![New Webhook](/emails/media/sparkpost_webhook_2.png "New webhook")

3) Renseignez l'URL cible avec `http://your-mautic.com/mailer/sparkpost/callback`

4) Sélectionnez les événements suivants

![Events](/emails/media/sparkpost_webhook_3.png "Events")

## Amazon Webhook
Mautic supporte les rebonds et plaintes depuis Amazon Simple Email Service (Amazon SES).

1) Allez sur votre compte Amazon Simple Notification Service (SNS) et créer un nouveau "topic"

![Topic](/emails/media/amazon_webhook_1.png "Create topic")

![Topic](/emails/media/amazon_webhook_2.png "Name your topic")

2) Cliquez sur le nouveau "topic" et créez un "subscriber"

![Topic](/emails/media/amazon_webhook_3.png "Go to the topic")

![Topic](/emails/media/amazon_webhook_4.png "New subscriber")

3) Entrez l'URL vers Amazon webhook sur votre installation Mautic

![Topic](/emails/media/amazon_webhook_5.png "Enter url to Mautic")

4) L'abonné gardera son statut en attente jusqu'à confirmation. AWS appelera la webhook Amazon avec une requête SubscriptionConfirmation incluant l'URL de callback. Pour confirmer, Mautic enverra une requête en retour pour valider l'abonnement. Soyez sûrs que votre installation Mautic puisse se connecter à internet, autrement les statuts resteront en attente et cela ne fonctionnera pas. Vérifiez le fichier de logs pour plus d'informations.

![Topic](/emails/media/amazon_webhook_6.png "Confirmation pending")

5) La dernière étape est de configurer Amazon SES pour délivrer les rebonds en utilisant votre topic SNS.

![Topic](/emails/media/amazon_webhook_7.png "Configure Amazon SES")

![Topic](/emails/media/amazon_webhook_8.png "Select SNS topic")

## Mailjet Webhook

Mautic supporte les webhooks Mailjet pour les bounces, spam et blockes. Avant toute configration, créez vous un compte sur [Mailjet](http://www.mailjet.com/).

1) Connectez vous à votre compte Mailjet et rendez vous dans "My Account" -> "Event tracking" (triggers)

![Webhooks](/emails/media/mailjet_webhook_1.png "Mailjet webhooks")

2) Dans la liste des types d'événements, sélectionnez ceux que vous souhaitez remonter dans votre compte Mautic

![Add Webhook](/emails/media/mailjet_webhook_2.png "Add webhook")

3) Mautic 2.2.0 supporte les webhooks suivantes : Message is Bounced, Message is Blocked, Message is Spam.

4) Renseignez les zones URL comme suivant `http://your-mautic.com/mailer/mailjet/callback`.
