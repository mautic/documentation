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
5. Wait for the `app/console mautic:leadlists:update` command to be automatically triggered by a cron job or execute it manually.

All leads with bounced emails should appear in this list.

## Mandrill Webhook

Mautic supports a few of Mandrill's webhooks for bounces.  

1) Login to your Mandrill account and go to Settings -> Webhooks

![Webhooks](/emails/media/mandrill_webhook_1.png "Mandrill webhooks")
 
2) Click Add a Webhook
 
![Add Webhook](/emails/media/mandrill_webhook_2.png "Add webhook")

3) Mautic 1.2.2 supports the following webhooks: Message is Bounced, Message is Soft-Bounced, Message is Rejected.  As of 1.2.3, Message is Marked as Spam and Message Recipient Unsubscribes will be supported.

4) Fill in the Post To Url as `http://your-mautic.com/mailer/mandrill/callback` then click Create Webhook. 

5) Click Custom Metadata and create two new metadata fields: `hashId` and `leadId`

![Add metadata](/emails/media/mandrill_webhook_5.png "Add metadata")

![Add metadata](/emails/media/mandrill_webhook_4.png "Add metadata")