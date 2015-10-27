# Monitored Email
Since version 1.2.0 Mautic has provided a feature which allows monitoring of IMAP accounts to detect bounced emails and unsubscribe requests.

## Monitored Inbox Settings
To use the Monitored email feature you must have the PHP IMAP extension enabled (most shared hosts will already have this turned on).  Simply go to the Mautic configuration and fill in the account details for the inbox(es) you wish to monitor.

![Monitored inbox settings](/emails/media/asset-monitored-inbox-settings.png "Monitored inbox settings")

It is possible to use a single inbox, or to configure a unique inbox per monitor.

To fetch and process the messages, run the following command:

```
php app/console mautic:fetch:email
```

Note that it is best to create an email specifically for this purpose, as Mautic will read each message it finds in the given folder. 

If sending mail through Gmail, the Return Path of the email will automatically be rewritten as the Gmail address. It is best to use a sending method other than Gmail, although Mautic can monitor a Gmail account for bounces.

If you select an Unsubscribe folder, Mautic will also append the email as part of the "List-Unsubscribe" header. It will then parse messages it finds in that folder and automatically unsubscribe the lead.