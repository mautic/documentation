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

If you select an Unsubscribe folder, Mautic will also append the email as part of the "List-Unsubscribe" header. It will then parse messages it finds in that folder and automatically unsubscribe the contact.

## Create a segment with bounced emails

This is not required, but if you'll want to be able to select the contacts with bounced emails easily for example to delete all bounced contacts, create the segment with bounced emails.

1. Go to *Segments* / *New*.
2. Type in the segment name. For example *Bounced emails*.
3. Select the *Filters* tab.
4. Create new *Bounced Email* equals Yes filter.
5. Wait for the `app/console mautic:segments:update` command to be automatically triggered by a cron job or execute it manually.

All contacts with bounced emails should appear in this segment.

## Mandrill Webhook

Mautic supports a few of Mandrill's webhooks for bounces.  

1) Login to your Mandrill account and go to Settings -> Webhooks

![Webhooks](/emails/media/mandrill_webhook_1.png "Mandrill webhooks")
 
2) Click Add a Webhook
 
![Add Webhook](/emails/media/mandrill_webhook_2.png "Add webhook")

3) Mautic 1.2.2 supports the following webhooks: Message is Bounced, Message is Soft-Bounced, Message is Rejected.  As of 1.2.3, Message is Marked as Spam and Message Recipient Unsubscribes will be supported.

4) Fill in the Post To Url as `http://your-mautic.com/mailer/mandrill/callback` then click Create Webhook. 

5) Click Custom Metadata and create two new metadata fields: `hashId` and `contactId`

![Add metadata](/emails/media/mandrill_webhook_5.png "Add metadata")

![Add metadata](/emails/media/mandrill_webhook_4.png "Add metadata")

## Sparkpost Webhook

1) Login to your Sparkpost account and go to Account -> Webhooks.

![Webhooks](/emails/media/sparkpost_webhook_1.png "Sparkpost webhooks")

2) Click the New Webhook button top right

![New Webhook](/emails/media/sparkpost_webhook_2.png "New webhook")

3) Fill in the Target URL as `http://your-mautic.com/mailer/sparkpost/callback`

4) Select the following Events

![Events](/emails/media/sparkpost_webhook_3.png "Events")

## Amazon Webhook
Mautic supports the bounce and complaint management from Amazon Simple Email Service (Amazon SES).

1) Go to the Amazon Simple Notification Service (SNS) and create a new topic

![Topic](/emails/media/amazon_webhook_1.png "Create topic")

![Topic](/emails/media/amazon_webhook_2.png "Name your topic")

2) Click on the newly created topic to create a subscriber

![Topic](/emails/media/amazon_webhook_3.png "Go to the topic")

![Topic](/emails/media/amazon_webhook_4.png "New subscriber")

3) Enter the url to the Amazon webhook on your Mautic installation

![Topic](/emails/media/amazon_webhook_5.png "Enter url to Mautic")

4) The subscriber will be in the pending state till it is confirmed. AWS will call your Amazon webhook with a SubscriptionConfirmation request including a callback url. To confirm Mautic will send a request back to this callback url to validate the subscription. Therefore make sure your Mautic installation is allowed to connect to the internet, otherwise the subscription will remain in the pending state and won't work. Check the logfile for more information.

![Topic](/emails/media/amazon_webhook_6.png "Confirmation pending")

5) The last step is to configure Amazon SES to deliver bounce and complaint messages using our SNS topic.

![Topic](/emails/media/amazon_webhook_7.png "Configure Amazon SES")

![Topic](/emails/media/amazon_webhook_8.png "Select SNS topic")


