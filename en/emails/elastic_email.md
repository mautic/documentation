# Elastic Email

Elastic Email [offer 150 000 emails/month](https://elasticemail.com/pricing)  for free. Mautic integrate Elastic Email SMTP and bounce notification.

## Elastic Email 

1) Create account. If you want use Elastic Email for more websites, create subaccount for each website.
 
2) Go to Settings > Domain and setup your sender domains.

[How To Validate Your Domain](https://elasticemail.com/support/account-setup/your-domain)

3) Go to Settings > SMTP/API and copy User name/Passowrd from SMTP  Configuration to Mautic.

## Webhook/Notification

1) Login to your Elastic Email account and go to Settings -> Notification.

2) Fill in the Notification URL as http://your-mautic-url.tld/mailer/elasticemail/callback

3) Check  these actions:  Unsubscribed, Complaints, Bounce/Error

![Webhooks](/emails/media/elasticemail_webhook_1.png "Elastic Email notification")

## Links

[Elastic Email Help & Support](https://elasticemail.com/support)
[Support via email](http://support.elasticemail.com/)
