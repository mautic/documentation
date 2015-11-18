# Mailchimp integration

Mautic can send leads to Mailchimp upon some lead's action or when it gain some point limit. Mailchimp can be also used as an email sending system. This option is not part of the plugin though so it will not be covered on this page.

## Authorize the plugin

Authorize the Mautic - Mailchimp plugin with the credentials you use to log in to the Mailchimp account. Username and password.

## Configure the plugin

Navigate to the *Features* tab in the plugin configuration modal box. You should see this note:

> The Lead Field Mapping tab will appear after selecting a list and will update after changing the selected list.

Select the lead list then. If you don't have the lead list created yet, go to *Lads* / *Manage Lists* and create one.

![Mailchimp Plugin configuration](/plugins/media/plugins-mailcimp-configure.png "Mailchimp Plugin configuration")

Other configuration options are:
- **Push leads to this integration** - This option is checked by default. If you uncheck it, the plugin will not push leads to Mailchimp any more.
- **Enable double opt in** - If Mailchimp should send a confirmation email to the leads added by this plugin. The leads will have to confirm that they really want to be added to the list.
- **Send welcome email** - Whether Mailchimp should sent the welcome email.

Configure the [field mapping](/plugins/field_mapping.html).

## Test the plugin

Follow [these steps]([field mapping](/plugins/integration_test.html) to test the integration.