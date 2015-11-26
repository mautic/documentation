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

## Create the list of leads with bounced emails

This is not required, but if you'll want to be able to select the leads with bounced emails easily for example to delete all bounced leads, create the lead list with bounced emails.

1. Go to *Leads* / *Manage Lists* / *New*.
2. Type in the list name. For example *Bounced emails*.
3. Select the *Filters* tab.
4. Create new *Bounced Email* equals Yes filter.
5. Wait for the `app/console mautic:list:update` command to be automatically triggered by a cron job or execute it manually.

All leads with bounced emails should appear in this list.
