# Mautic - Zoho CRM plugin

This plugin can push a lead to Zoho CRM when a lead makes some action.

If you don't have the Zoho CRM account yet, [create it](https://www.zoho.com/crm/).

## Configure the Zoho CRM plugin

Insert the email and password you created the Zoho account with into the Mautic Zoho integration plugin and authorize it. Set the *Publish* switch to *Yes*. Save.

![Zoho CRM Plugin configuration](/plugins/media/plugins-zoho-authorization.png "Zoho CRM Plugin configuration")

If Zoho Two Factor Authentication is enabled, an Application Specific Password will need to be generated and used.
(https://www.zoho.com/mail/help/adminconsole/two-factor-authentication.html#alink5)

In the Features tab is just *Push leads to this integration* checkbox and it is checked by default.

Configure the [field mapping](./../plugins/field_mapping.html).

Save the plugin configuration.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.
